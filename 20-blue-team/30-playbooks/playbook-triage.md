# SOC Triage Playbook

**Short description (EN):**  
This playbook describes the initial triage process in a SOC environment.  
Its goal is to quickly classify an alert, assess urgency, and route it to the appropriate detailed playbook (brute force, phishing, endpoint, etc.).  
It is tool-agnostic and focuses on analytical thinking rather than interface navigation.

---

# Playbook: SOC Triage (до конкретных playbook'ов)

## Цель

Быстро (1–5 минут) определить:

1. Что это за тип алерта  
2. Есть ли признаки успеха / ущерба  
3. В какой конкретный playbook перейти (brute force / phishing / suspicious PowerShell / ...)

Это этап ДО глубокого расследования.

---

## Alert Passport (зафиксировать сразу)

- Alert name / Rule name:
- Severity:
- Time window:
- Primary entities (что главное): user / host / IP / email / url / process
- Data source: Windows / Linux / EDR / Email / Proxy / Cloud / Firewall

---

## Step 0 — Sanity Check (качество алерта)

Проверить:

- Это не тест / maintenance?
- Это не известный scanner / monitoring / service account?
- Правило понятно? (что именно считается аномалией?)

### Решение:

- Если явно false positive → закрыть как FP (с объяснением)
- Если не очевидно → продолжаем triage

---

## Step 1 — Классификация по сущностям (Routing)

Определи ветку по тому, какие сущности доминируют.

---

### A) Identity / Authentication

Сущности:
- user
- failed logins
- source IP
- host
- logon type

→ Переход в: `playbook-bruteforce.md`

(в будущем: password spray / impossible travel / MFA abuse)

---

### B) Email

Сущности:
- sender
- recipient
- subject
- URL
- attachment
- message-id

→ Переход в: `playbook-phishing.md`

---

### C) Endpoint / EDR

Сущности:
- host
- process name
- command line
- parent process
- hash

→ Переход в: suspicious PowerShell / malware execution / persistence

---

### D) Network / Perimeter

Сущности:
- source IP
- destination IP
- port
- protocol
- domain
- bytes transferred

→ Переход в: scan / C2 / exfiltration playbooks

---

### E) Cloud / SaaS

Сущности:
- user
- application
- sign-in event
- geo-location
- MFA
- token activity

→ Переход в: cloud authentication anomaly playbook

---

## Step 2 — Срочность (есть ли успех или ущерб?)

Главный вопрос:

> Уже получилось? Или это только попытки?

---

### Для Authentication

- Есть ли successful login после failed?
- Есть ли необычный Logon Type?
- Есть ли новые сессии (RDP / SSH)?

---

### Для Email

- Был ли click?
- Было ли открытие вложения?
- Есть ли execution на endpoint?

---

### Для Endpoint

- Есть ли запуск подозрительного процесса?
- Есть ли privilege escalation?
- Есть ли persistence?

---

### Для Network

- Есть ли подтверждённый C2?
- Есть ли передача данных наружу?
- Есть ли lateral movement?

---

### Решение:

- Есть признаки успеха / ущерба → Escalate (Incident / High Suspicious)
- Только попытки → продолжить расследование в конкретном playbook

---

## Step 3 — Минимальный контекст

Перед переходом глубже проверить:

- Критичность пользователя (admin? service account?)
- Критичность хоста (server? DC? workstation?)
- Internal или external источник?
- Была ли подобная активность раньше?

---

## Step 4 — Переход в конкретный playbook

После triage ты должен оставить в тикете:

- Категорию (Auth / Email / Endpoint / Network / Cloud)
- Почему отнёс к этой категории
- Есть ли признаки успеха
- Уровень срочности
- Какой playbook выбран дальше

---

# Важно

Triage ≠ расследование.

Triage — это:

быстро понять  
не паниковать  
не игнорировать  
и правильно направить анализ.