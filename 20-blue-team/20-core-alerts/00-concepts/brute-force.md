# Brute Force (перебор паролей)

## 1) Что это такое (Definition)
**Brute Force** — попытка получить доступ к учетной записи путём перебора множества паролей для **одного пользователя** (Single Username → Many Passwords).

Частый “родственник”, который важно отличать:
- **Password Spray** — один/несколько популярных паролей по **многим пользователям** (Many Users → One Password).

---

## 2) Как выглядит в логах (How it looks in logs)
Типовой паттерн:
- много событий **Failed Login** за короткий промежуток времени
- один `Username` и часто один `Source IP`
- иногда после серии неудач появляется **Successful Login**

### Windows (часто в SOC)
- **4625** — Failed Logon (неуспешная аутентификация)
- **4624** — Successful Logon (успешная аутентификация)

Ключевые поля (Common fields):
- `TargetUserName` / `Account Name` (Username)
- `IpAddress` / `Source Network Address` (Source IP)
- `LogonType` (тип входа: интерактивный/сетевой/RDP и т.д.)
- `FailureReason` / `Status` / `SubStatus` (почему неудача)
- `WorkstationName` / `Computer` (Host)

---

## 3) Отличие от Password Spray (Brute Force vs Spray)
### Brute Force
- **один** пользователь
- **много** паролей
- может быть быстрым (burst) или **low-and-slow** (медленно, но долго)

### Password Spray
- **много** пользователей
- **1–3** пароля (обычно)
- часто распределено во времени, чтобы обходить lockout policy

---

## 4) Типовые сценарии (Common scenarios)
### Злоумышленник (Malicious)
- внешний IP или TOR/VPN/Hosting ASN
- много попыток, высокая частота или медленная “стелс” частота
- после успешного входа может начаться:
  - RDP/SMB activity
  - lateral movement
  - privilege escalation

### Ложноположительное / benign (False Positive / Benign)
Очень частый кейс:
- **service account** / служебная учётка
- строго регулярные интервалы (каждые 5/10/15 минут)
- внутренний хост (internal IP)
- нет признаков “post-authentication activity”

Причина: пароль поменяли, а в сервисе/таске остался старый пароль.

---

## 5) Мини-алгоритм расследования (Investigation workflow)
Это концептуальные шаги (почему и что проверяем). Конкретные клики будут в `10-siem-interface`.

### Шаг A — Контекст (Context)
- откуда алерт (Alert Source): SIEM/EDR/AD logs
- кто затронут (Affected user)
- откуда (Source IP)
- когда (Time range)
- какой сервис/протокол (SSH/RDP/OWA/VPN/etc)

### Шаг B — Подтвердить паттерн (Validate pattern)
- один пользователь vs много пользователей
- частота попыток (burst или low-and-slow)
- есть ли блокировки аккаунта (Account lockout)

### Шаг C — Проверить успешную аутентификацию (Check success)
- есть ли **4624 Successful Logon** после серии **4625**
- совпадает ли `Source IP`
- совпадает ли время

### Шаг D — Проверить “что было после” (Post-authentication activity)
Если successful login был:
- появились ли новые сессии (New sessions)
- RDP/SMB/WinRM activity
- доступ к файловым ресурсам
- новые процессы (например PowerShell)
- outbound connections (внешние соединения)

### Шаг E — IOC & риск (IOC validation & risk)
- репутация IP (Reputation)
- internal vs external
- ASN / hosting provider
- таргет: privileged account? service account?

---

## 6) Критерии классификации (Decision criteria)
### Likely False Positive / Benign
- internal IP + service account
- регулярный интервал (как cron)
- нет успешной интерактивной сессии
- нет пост-активности после успешного логина

### Suspicious
- внешний IP, но нет успеха
- необычное время/гео/ASN
- попытки по важной учетке (admin/service account)

### Confirmed Incident
- successful login после серии failed + признаки пост-активности
- lateral movement indicators
- доступ к критичным ресурсам

---

## 7) Уровень критичности (Severity hints)
- **Low**: failed-only, внешний IP, неуспешно, без масштаба
- **Medium**: длительная атака / много попыток / важный аккаунт
- **High**: есть successful login + post-authentication activity / lateral movement

---

## 8) Что документировать (What to record for ticket)
Минимальный набор для тикета:
- alert id / rule name
- username / host
- source IP + reputation results
- counts (сколько failed, за какой период)
- был ли successful login (да/нет)
- что проверил по post-activity
- решение: FP / Suspicious / Incident + причина

---

## Связь с Playbook
- **Playbook** (30-playbooks) = “что делать кратко”
- **Concept** (этот файл) = “почему это делать и как отличать сценарии”
- **Case** (10-cases) = “как это выглядело в конкретной комнате + скрины/запросы”