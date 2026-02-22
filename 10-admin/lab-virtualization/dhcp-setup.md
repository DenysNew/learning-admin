# DHCP Setup (srv-dc01)

## Цель

Настроить DHCP-сервер на srv-dc01 для автоматической выдачи IP-адресов клиентам внутренней сети lab-net.

---

## Контекст лаборатории

Hypervisor: VirtualBox  
Network: lab-net (Internal Network)  
DHCP Server: srv-dc01  
OS: Windows Server 2022  

Network: 10.10.10.0/24  

---

## Установка роли DHCP

### Запуск мастера установки

![DHCP Role Install Wizard](../../images/lab-virtualization/dhcp/dhcp-role-install-wizard-start.png)

---

### Выбор роли DHCP Server

![DHCP Role Selected](../../images/lab-virtualization/dhcp/dhcp-role-selected.png)

---

### Установка завершена

![DHCP Role Install Complete](../../images/lab-virtualization/dhcp/dhcp-role-install-progress.png)

---

## Post-install configuration

![DHCP Post Install Wizard](../../images/lab-virtualization/dhcp/dhcp-postinstall-wizard.png)

---

## Создание Scope

Scope Name: lab-net  
Network: 10.10.10.0/24  
Range: 10.10.10.100 – 10.10.10.200  
Exclusions: 10.10.10.10  
DNS: 10.10.10.10  
Domain: lab.local  

---

### Scope активен

![DHCP Scope Active](../../images/lab-virtualization/dhcp/dhcp-scope-active.png)

---

## Проверка DHCP Manager

![DHCP Manager Opened](../../images/lab-virtualization/dhcp/dhcp-manager-opened.png)

---

## Проверка клиентов

Windows:

ipconfig /release  
ipconfig /renew  
ipconfig /all  

Linux:

ip a  
ip route  

---

## Результат

DHCP Server установлен и работает.

srv-dc01 выдает IP адреса клиентам lab-net.

## Полные артефакты установки и настройки DHCP

Все скриншоты всех этапов установки, конфигурации и создания Scope находятся в каталоге:

📁 [images/lab-virtualization/dhcp/](../../images/lab-virtualization/dhcp/)

В каталоге содержатся:

- установка роли DHCP
- DHCP Post-Install Configuration
- создание Scope
- настройка DNS и параметров Scope
- активация Scope
- DHCP Manager и итоговая конфигурация

Это полный журнал установки и настройки DHCP-сервера в лабораторной среде.