# Week 0 — Daily Plan (Home Lab Setup)

Принцип:
- 1–2 часа в день
- Каждый день = конкретный результат
- Всё фиксируется в Git-репо

---

## День 1 — Подготовка хоста + гипервизор

Цель:
Чтобы среда была готова.

Сделать:
- Установить VirtualBox или VMware
- Скачать ISO:
  - Ubuntu Server LTS
  - Windows Server (Evaluation)
  - Windows 10/11
- Зафиксировать:
  - гипервизор
  - версии ISO
  - железо хоста (CPU / RAM / диск)

Артефакт:
- `README.md`:
  - гипервизор
  - ISO версии
  - характеристики хоста

---

## День 2 — Создание VM

Цель:
Поднять базовые машины.

Сделать:
- Создать 3 VM:
  - ubuntu-srv
  - win-server
  - win-client
- Настроить:
  - CPU: 2
  - RAM: 2–4 GB
- Сетевые адаптеры:
  - Adapter 1: NAT
  - Adapter 2: Host-Only или Internal

Артефакт:
- Таблица VM:
  - имя
  - CPU
  - RAM
  - диск
  - сети

---

## День 3 — Установка ОС

Цель:
Чтобы все 3 VM загрузились.

Сделать:
- Ubuntu Server:
  - minimal install
  - OpenSSH Server = YES
- Windows Server:
  - Desktop Experience
- Windows Client

Артефакт:
- Скриншоты login-экрана всех 3 VM
- `README.md`:
  - какие пользователи
  - какие пароли (обезличено!)

---

## День 4 — Сети и статические IP

Цель:
Чтобы внутренняя сеть реально работала.

Сделать:
- Диапазон:
  - 10.10.10.0/24
- Назначить IP:
  - Ubuntu: 10.10.10.10
  - Win Server: 10.10.10.20
  - Win Client: 10.10.10.30
- Проверить:
  - ping между всеми
  - доступ в интернет через NAT

Команды (Ubuntu):

ip a  
ip r  
ping 10.10.10.20  
ping 8.8.8.8  

Артефакт:
- Таблица IP
- Скрины ping

Системное мышление:
- Где NAT?
- Где Internal?
- Какие пути трафика?

---

## День 5 — Linux: пользователи, группы, sudo

Цель:
Начать неделю 1.

Сделать:
- Создать пользователей:

sudo useradd -m admin  
sudo useradd -m user  
sudo useradd -m auditor  

- Пароли:

sudo passwd admin  
sudo passwd user  
sudo passwd auditor  

- Группы:

sudo groupadd appadmins  
sudo usermod -aG appadmins admin  

- sudo только для одного сервиса (nginx):

sudo visudo  

Добавить:

user ALL=NOPASSWD: /bin/systemctl restart nginx  

Артефакт:
- `10-admin/linux/01-users-groups.md`:
  - команды
  - объяснение sudo-прав

---

## День 6 — Права и структура каталогов

Цель:
Закрепить файловые права.

Сделать:

sudo mkdir -p /srv/app/{configs,data,logs}  
sudo chown -R admin:appadmins /srv/app  
sudo chmod -R 750 /srv/app  

Проверка:

ls -ld /srv/app  
ls -ld /srv/app/*  

Артефакт:
- Скрины ls -ld
- README:
  - почему такие права

Системное мышление:
- Где хранятся данные?
- Кто им доверен?

---

## День 7 — Поиск, grep, find, мини-чеклист

Цель:
Закрыть неделю 1.

Сделать:

Найти все .conf в /etc:

sudo find /etc -name "*.conf"  

Найти строки PermitRootLogin:

sudo grep -R "PermitRootLogin" /etc/ssh  

Мини-чеклист:
- как найти файл
- как найти строку
- как проверить владельца

Артефакт:
- Чеклист
- Примеры команд

Системное мышление:
- Как быстро найти следы атаки?
- Где искать конфиги?