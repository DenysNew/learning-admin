# Linux File Permissions и Special Bits

## 1. Структура прав доступа

Пример:

    -rwxr-xr-x 1 root root backup.sh

Структура:

    [file type][owner][group][others]

Разбор:

    - rwx r-x r-x
    │ │   │   │
    │ │   │   └── права others (другие пользователи)
    │ │   └────── права group (группа)
    │ └────────── права owner (владелец)
    └──────────── тип файла

---

## 2. Типы файлов

Первый символ показывает тип файла:

    -  = обычный файл (regular file)
    d  = директория (directory)
    l  = символическая ссылка (symbolic link)

Примеры:

    -rw-r--r-- file.txt
    drwxr-xr-x Documents/
    lrwxrwxrwx link -> /etc/passwd

---

## 3. Обозначения прав доступа

Каждый блок содержит 3 символа:

    r = read (чтение)
    w = write (запись)
    x = execute (выполнение)
    - = нет права

Примеры:

    rwx = чтение, запись, выполнение
    r-x = чтение, выполнение
    r-- = только чтение

---

## 4. Категории пользователей

Есть три категории:

    owner  = владелец файла
    group  = пользователи группы файла
    others = все остальные пользователи

Пример:

    -rwxr-xr--

означает:

    owner: read, write, execute
    group: read, execute
    others: read

---

## 5. Числовые (numeric) permissions

Каждому праву соответствует число:

    r = 4
    w = 2
    x = 1

Суммируем:

    rwx = 7
    r-x = 5
    r-- = 4

Пример:

    -rwxr-xr-x

numeric:

    755

---

## 6. Special permissions (важно для pentest)

Специальные биты:

    SUID   = 4000
    SGID   = 2000
    Sticky = 1000

Полный формат numeric permissions:

    [special][owner][group][others]

Пример:

    4755

---

## 7. SUID (Set User ID)

Пример:

    -rwsr-xr-x 1 root root backup

"s" заменяет execute у owner:

    rws

Это означает:

Файл выполняется с правами владельца.

Если владелец root → файл выполняется как root.

---

Почему это важно для pentester:

Если SUID файл уязвим → можно получить root доступ.

Поиск SUID файлов:

    find / -perm -4000 2>/dev/null

---

## 8. SGID (Set Group ID)

Пример:

    -rwxr-sr-x

Numeric:

    2755

Файл выполняется с правами группы.

---

## 9. Sticky bit

Пример:

    drwxrwxrwt

Numeric:

    1777

Используется, например, для:

    /tmp

Пользователь может удалять только свои файлы.

---

## 10. Пример numeric permissions

    4755

Разбор:

    4 = SUID
    7 = owner rwx
    5 = group r-x
    5 = others r-x

Symbolic форма:

    -rwsr-xr-x

---

## 11. Команды для работы с permissions

Показать permissions:

    ls -la

Показать numeric:

    stat filename

Изменить permissions:

    chmod 755 filename

Установить SUID:

    chmod 4755 filename

---

## 12. Команды, важные для pentest

Поиск SUID:

    find / -perm -4000 2>/dev/null

Поиск writable:

    find / -writable 2>/dev/null

---

## 13. Почему это важно для privilege escalation

SUID файлы могут выполняться как root.

Если файл уязвим → можно получить root shell.

Это один из основных методов privilege escalation.

---

## 14. Summary

Permissions состоят из:

    file type
    owner
    group
    others
    special permissions

Numeric:

    4755

Symbolic:

    -rwsr-xr-x

SUID позволяет выполнять файл с правами владельца (например root).


---

## Практика

Практическая демонстрация и артефакты:

[linux-file-permissions.md](./file-permissions.md)
