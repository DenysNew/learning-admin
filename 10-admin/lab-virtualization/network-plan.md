# План сети (Network Plan)

## Цель

Этот документ описывает сетевую архитектуру лабораторной среды VirtualBox.

Цели:

- изолировать лабораторную сеть
- обеспечить интернет-доступ для обновлений
- создать воспроизводимую инфраструктуру
- зафиксировать конфигурацию сети как артефакт

---

## Сегменты сети

В лаборатории используются два сетевых сегмента:

### 1. NAT (доступ в интернет)

Назначение:

- обновление системы
- установка пакетов
- доступ к внешним ресурсам
- загрузка инструментов

Характеристики:

- предоставляется VirtualBox автоматически
- типичная сеть: `10.0.2.0/24`
- шлюз: `10.0.2.2`
- IP назначается через DHCP VirtualBox

---

### 2. Internal Network: `lab-net` (внутренняя лабораторная сеть)

Назначение:

- связь между виртуальными машинами
- Active Directory лаборатория
- тестирование атак
- изолированная среда

Характеристики:

- полностью изолирована от внешней сети
- доступ только между VM внутри `lab-net`
- интернет отсутствует

---

## Конфигурация виртуальных машин

Все виртуальные машины используют:

- Adapter 1: Internal Network (`lab-net`)
- Adapter 2: NAT

---

## Артефакты: настройки сети VirtualBox

### Kali Linux

Internal Network:

![kali lab-net](../../images/lab-virtualization/vm-settings/kali-attacker01-network-lab-net.png)

NAT:

![kali nat](../../images/lab-virtualization/vm-settings/kali-attacker01-network-nat.png)

---

### Windows Server (srv-dc01)

Internal Network:

![srv-dc01 lab-net](../../images/lab-virtualization/vm-settings/srv-dc01-network-lab-net.png)

NAT:

![srv-dc01 nat](../../images/lab-virtualization/vm-settings/srv-dc01-network-nat.png)

---

### Ubuntu Server

Internal Network:

![ubuntu lab-net](../../images/lab-virtualization/vm-settings/ubuntu-server-network-lab-net.png)

NAT:

![ubuntu nat](../../images/lab-virtualization/vm-settings/ubuntu-server-network-nat.png)

---

### Windows Client (ws-client01)

Internal Network:

![ws-client lab-net](../../images/lab-virtualization/vm-settings/ws-client01-network-labnet.png)

NAT:

![ws-client nat](../../images/lab-virtualization/vm-settings/ws-client01-network-nat.png)

---

## Проверка сети (Kali Linux)

### IP адрес

![ip a](../../images/lab-virtualization/network-tests/kali-ip-a.png)

---

### Таблица маршрутизации

![ip route](../../images/lab-virtualization/network-tests/kali-ip-route.png)

---

### Проверка доступа в интернет (IP)

![ping 8.8.8.8](../../images/lab-virtualization/network-tests/kali-ping-8.8.8.8.png)

---

### Проверка DNS

![ping google](../../images/lab-virtualization/network-tests/kali-ping-google.png)

---

## Итоговая архитектура

            INTERNET
               |
          VirtualBox NAT
               |
   +-----------+-----------+
   |           |           |
  Kali      Windows      Ubuntu
               |
            Windows Client



## Итог

Лабораторная сеть успешно настроена:

- internet доступ через NAT — работает
- внутренняя сеть lab-net — настроена
- виртуальные машины подключены корректно
- конфигурация зафиксирована артефактами