# Linux: анализ прав доступа и SUID

Практика в учебной среде: чтение владельца и групп прав, проверка системной программы `passwd`, поиск файлов с SUID и разбор отдельного учебного бинарного файла.

## Что проверялось

- `ls -la`: тип файла, владелец, группа и права.
- `ls -la /usr/bin/passwd`: пример системного исполняемого файла с SUID.
- `find / -perm -4000 2>/dev/null`: перечень объектов с установленным SUID.
- `ls -la /home/user3/shell`: права конкретного файла в учебной среде.

Скриншоты ниже подтверждают просмотр прав и результаты поиска. Сам список SUID-файлов не доказывает получение повышенных привилегий. Для оценки риска нужно отдельно анализировать программу, её владельца и доступность записи.

[Краткая справка: права, SUID, SGID и sticky bit](file-permissions.md)

## Артефакты

## Basic permissions overview

Command:

    ls -la

![Basic permissions](./artifacts/permissions/01-basic-permissions.png)

---

## System SUID example

Command:

    ls -la /usr/bin/passwd

![System SUID passwd](./artifacts/permissions/02-system-suid-passwd.png)

---

## SUID enumeration

Command:

    find / -perm -4000 2>/dev/null

![Find SUID files](./artifacts/permissions/03-find-suid-files.png)

---

## User SUID binary example

Command:

    ls -la /home/user3/shell

![User SUID binary](./artifacts/permissions/04-user-suid-binary.png)
