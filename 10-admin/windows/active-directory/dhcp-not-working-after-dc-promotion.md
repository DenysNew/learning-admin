# DHCP Not Working After Domain Controller Promotion

## Description (EN)

Troubleshooting case where DHCP stopped working after promoting a Windows Server to a Domain Controller in a VirtualBox lab environment.

The issue caused clients to receive APIPA addresses and prevented domain communication. This document describes the symptoms, diagnostics, root cause and resolution.

---

## Контекст лаборатории

Гипервизор: VirtualBox  
Сеть: Internal Network `lab-net`  

Инфраструктура:

| Host | Role |
|-----|-----|
| srv-dc01 | Domain Controller + DNS + DHCP |
| ws-client01 | Windows Client |
| ubuntu-srv | Ubuntu Server |

Домен:

lab.local

---

## Проблема

После повышения Windows Server до Domain Controller DHCP перестал выдавать IP-адреса клиентам.

Windows клиент получал APIPA адрес из диапазона `169.254.x.x`, что означает отсутствие DHCP сервера.

Linux сервер также не получал IP адрес из сети лаборатории.

---

## Симптомы

### Клиент получает APIPA адрес

![APIPA address](artifacts/dhcp-after-dc-promotion/client-apipa-address-no-dhcp.png)

---

### Невозможно связаться с контроллером домена

![Client cannot reach DC](artifacts/dhcp-after-dc-promotion/client-cannot-reach-domain-controller.png)

---

### DNS запросы не работают

![DNS timeout](artifacts/dhcp-after-dc-promotion/client-ipconfig-and-dns-timeout.png)

---

### Невозможно войти в домен

![Domain login failed](artifacts/dhcp-after-dc-promotion/domain-login-failed-domain-not-available.png)

---

## Диагностика

При проверке DHCP сервера было обнаружено, что IPv4 сервис не активирован.

![DHCP IPv4 not active](artifacts/dhcp-after-dc-promotion/dhcp-ipv4-not-active.png)

---

Также были проверены настройки DHCP scope и DNS параметров.

![DHCP scope options](artifacts/dhcp-after-dc-promotion/dhcp-scope-options-dns-settings.png)

---

## Причина

После повышения сервера до Domain Controller DHCP IPv4 сервис оказался неактивным.

Из-за этого DHCP сервер не выдавал IP адреса клиентам.

---

## Решение

Был активирован DHCP IPv4 и перезапущена работа DHCP сервера.

После этого клиенты начали получать IP адреса из DHCP scope.

---

## Результат

### Windows клиент получил IP адрес

![Client received IP](artifacts/dhcp-after-dc-promotion/client-received-ip-from-dhcp.png)

---

### Успешный вход в систему

![Client login success](artifacts/dhcp-after-dc-promotion/client-login-after-dhcp-fix.png)

---

### Ubuntu сервер получил IP адрес от DHCP

![Ubuntu DHCP](artifacts/dhcp-after-dc-promotion/ubuntu-server-received-ip-from-dhcp.png)

---

## Итог

DHCP перестал работать из-за неактивного IPv4 сервиса после повышения сервера до Domain Controller.

После активации DHCP IPv4 клиенты начали корректно получать IP адреса и смогли взаимодействовать с доменом.