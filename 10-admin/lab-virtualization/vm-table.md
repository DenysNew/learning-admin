# Таблица виртуальных машин (VM Table)

## Назначение

Этот документ содержит список всех виртуальных машин лабораторной среды и их сетевые параметры.

Используется для:

- инвентаризации инфраструктуры
- планирования сети
- администрирования
- pentest задач

---

## Таблица виртуальных машин

| VM Name | Hostname | OS | Role | Network: lab-net | Network: NAT | Internet |
|--------|----------|----|------|------------------|--------------|----------|
| kali-attacker01 | kali-attacker01 | Kali Linux | Attacker machine | configured | configured | yes |
| srv-dc01 | srv-dc01 | Windows Server 2022 | Domain Controller (planned) | configured | configured | yes |
| ubuntu-server | ubuntu-server | Ubuntu Server | Linux server | configured | configured | yes |
| ws-client01 | ws-client01 | Windows 11 | Client machine | configured | configured | yes |

---

## Сетевая архитектура

Каждая VM имеет:

Adapter 1: Internal Network (lab-net)  
Adapter 2: NAT  

---

## Артефакты конфигурации сети

Скриншоты находятся:

[images/lab-virtualization/vm-settings/](../../images/lab-virtualization/vm-settings/)
---

## Статус

lab-net: configured  
NAT: configured  
Internet access: working  

DHCP server: not configured yet