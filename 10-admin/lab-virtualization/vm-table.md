# Таблица виртуальных машин (VM Table)

## Назначение

Этот документ содержит список всех виртуальных машин лабораторной среды и их сетевые параметры.

Используется для:

- инвентаризации инфраструктуры
- планирования сети
- администрирования
- pentest-задач

---

## Таблица виртуальных машин

| VM Name        | Hostname      | OS                  | Role                     | IP (lab-net)            | Тип адресации | NAT        | Internet |
|---------------|---------------|---------------------|--------------------------|--------------------------|---------------|------------|----------|
| srv-dc01      | srv-dc01      | Windows Server 2022 | Domain Controller / DNS / DHCP | 10.10.10.10 | Static | DHCP (10.0.2.x) | Yes |
| ws-admin01    | ws-admin01    | Windows 11          | Admin Workstation        | DHCP (10.10.10.100+)     | DHCP          | DHCP       | Yes |
| ws-client01   | ws-client01   | Windows 11          | Domain Client            | DHCP (10.10.10.100+)     | DHCP          | DHCP       | Yes |
| ubuntu-server | ubuntu-server | Ubuntu Server       | Linux Server             | DHCP (10.10.10.100+)     | DHCP          | DHCP       | Yes |
| kali-attacker01 | kali-attacker01 | Kali Linux      | Attacker Machine         | 10.10.10.50              | Static        | DHCP       | Yes |

---

## Политика адресации

### Внутренний сегмент (lab-net) — 10.10.10.0/24

Статические IP:
- 10.10.10.10 — srv-dc01 (Domain Controller, DNS)
- 10.10.10.50 — kali-attacker01

DHCP-пул:
- 10.10.10.100 – 10.10.10.200
- Раздаётся Windows Server (роль DHCP)

### NAT-сегмент — 10.0.2.0/24

- Все машины получают IP автоматически от VirtualBox NAT
- Default Gateway: 10.0.2.2
- Используется только для выхода в интернет

---

## Сетевая архитектура

Каждая VM имеет:

Adapter 1: NAT (Internet access)  
Adapter 2: Internal Network (lab-net)

Маршрутизация:

- Default route у машин с двумя интерфейсами направлен через NAT
- На внутреннем интерфейсе gateway не указывается
- DNS внутри домена указывает на 10.10.10.10

---

## Артефакты конфигурации сети

Скриншоты находятся:

[images/lab-virtualization/vm-settings/](../../images/lab-virtualization/vm-settings/)

---

## Статус

lab-net: configured and stable  
NAT: configured and stable  
Internet access: working  
DHCP (internal): configured on Windows Server  
Reboot test: passed