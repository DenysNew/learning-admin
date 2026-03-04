# AD DS Domain Controller (lab.local) + DHCP/DNS — настройка в лаборатории

**EN (short):** Promoted Windows Server to a Domain Controller, created a new forest `lab.local`, enabled DNS, and verified the domain join of `WS-CLIENT01` plus DHCP/DNS configuration.

---

## Цель
Развернуть Active Directory Domain Services (AD DS) и поднять **Domain Controller** для лабораторного домена `lab.local`, включая:
- создание нового forest `lab.local`
- установка ролей AD DS (+ DNS) и проверка
- подтверждение, что клиент `WS-CLIENT01` зарегистрирован в Active Directory
- подтверждение, что клиент получает корректные параметры DHCP/DNS

## Контекст лаборатории (кратко)
- Гипервизор: VirtualBox
- DC: `srv-dc01`
- Домен: `lab.local`
- NetBIOS: `LAB`
- Сеть: `lab-net` (Internal Network)
- План (пример):
  - DC/DNS/DHCP: `10.10.10.10`
  - Клиент: `10.10.10.101` (по DHCP)

---

## Артефакты (скриншоты)
Все скриншоты лежат в папке:

`artifacts/domain-controller/`

---

## 1. Установка роли AD DS
Открыть:
**Server Manager → Add Roles and Features**

### 1.1 Before you begin
![Before you begin](artifacts/domain-controller/add-roles-and-features-before-you-begin.png)

### 1.2 Выбор роли Active Directory Domain Services
Отмечаем роль **Active Directory Domain Services** (AD DS).

![Select AD DS role](artifacts/domain-controller/select-active-directory-domain-services-role.png)

### 1.3 Установка компонентов (progress)
![AD DS installation progress](artifacts/domain-controller/ad-ds-installation-progress.png)

---

## 2. Promote this server to a Domain Controller
После установки роли появится уведомление **Promote this server to a domain controller**.

![Promote server to domain controller](artifacts/domain-controller/promote-server-to-domain-controller.png)

---

## 3. Создание нового леса (New forest)
Выбираем:
- **Add a new forest**
- Root domain name: `lab.local`

![Create new forest](artifacts/domain-controller/create-new-forest-lab-local.png)

---

## 4. Domain Controller Options
Оставляем включенным:
- DNS server
- Global Catalog (GC)

Задаём пароль DSRM (Directory Services Restore Mode).

![Domain controller options](artifacts/domain-controller/domain-controller-options-dns-gc.png)

---

## 5. DNS Options (предупреждение о delegation)
Предупреждение про DNS delegation для лаборатории — нормально (часто появляется в isolated lab).

![DNS delegation warning](artifacts/domain-controller/dns-delegation-warning.png)

---

## 6. NetBIOS имя домена
Проверяем NetBIOS имя: `LAB`

![NetBIOS domain name](artifacts/domain-controller/netbios-domain-name-lab.png)

---

## 7. Пути баз данных AD DS
Оставляем пути по умолчанию (если нет требований менять):

![AD DS database paths](artifacts/domain-controller/ad-ds-database-paths.png)

---

## 8. Prerequisites Check
Проверяем prerequisites и запускаем установку.

![Prerequisites check](artifacts/domain-controller/ad-ds-prerequisites-check.png)

---

## 9. Установка и завершение (DC promotion)
### 9.1 Installation progress
![Domain controller installation progress](artifacts/domain-controller/domain-controller-installation-progress.png)

### 9.2 Успех и автоперезагрузка
![Domain controller installation success](artifacts/domain-controller/domain-controller-installation-success.png)

---

## 10. Проверка входа в домен на DC
После перезагрузки проверяем, что логин уже доменный (например `LAB\Administrator`).

![First domain login](artifacts/domain-controller/domain-controller-first-domain-login.png)

Дополнительно (проверка whoami):
![Domain user whoami](artifacts/domain-controller/domain-user-whoami.png)

---

## 11. Проверка IP на контроллере домена
DC имеет IP `10.10.10.10` в lab-net (и может иметь второй адаптер NAT — это нормально, если так задумано).

![Domain controller ipconfig](artifacts/domain-controller/domain-controller-ipconfig.png)

---

## 12. Подтверждение: компьютер WS-CLIENT01 зарегистрирован в AD
Открыть:
**Server Manager → Tools → Active Directory Users and Computers**
и проверить объект компьютера `WS-CLIENT01` в контейнере `Computers`.

![WS-CLIENT01 computer object](artifacts/domain-controller/domain-computer-object-ws-client01.png)

---

## 13. Подтверждение: DHCP/DNS параметры на клиенте (успешно)
На клиенте (`WS-CLIENT01`) проверяем `ipconfig /all` и убеждаемся, что:
- IPv4 из сети `10.10.10.0/24` (например `10.10.10.101`)
- DHCP Server: `10.10.10.10`
- DNS Servers: `10.10.10.10`

![Client ipconfig DHCP success](artifacts/domain-controller/domain-controller-ipconfig.png)


---

## Итог
- Создан новый forest `lab.local`
- `srv-dc01` успешно промотирован в Domain Controller
- DNS включен на DC
- `WS-CLIENT01` зарегистрирован в AD (есть компьютерный объект)
- Клиент получает корректные DHCP/DNS параметры от DC

---

## Следующий шаг (отдельный документ)
Проблемы вида “DHCP service выключена / клиент не получает IP / domain isn’t available” — оформляем отдельным файлом troubleshooting, чтобы не смешивать “успешный кейс” и “разбор инцидента”.