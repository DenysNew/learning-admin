# Git — краткая шпаргалка команд / Git — krótka ściąga / Git — short cheat sheet

---

## 🔹 Базовые команды / Podstawowe komendy / Basic commands

### Проверить статус репозитория

### Sprawdzić status repozytorium

### Check repository status

```bash
git status
```

### Посмотреть историю коммитов

### Zobaczyć historię commitów

### View commit history

```bash
git log --oneline
```

### Посмотреть изменения в файлах

### Zobaczyć zmiany w plikach

### View file changes

```bash
git diff
```

---

## 🔹 Работа с файлами и коммитами / Praca z plikami i commitami / Working with files and commits

### Добавить все изменения в Git

### Dodać wszystkie zmiany do Gita

### Add all changes to Git

```bash
git add .
```

### Добавить конкретный файл

### Dodać konkretny plik

### Add a specific file

```bash
git add путь/к/файлу
```

### Сделать коммит

### Zrobić commit

### Make a commit

```bash
git commit -m "Описание изменений"
```

---

## 🔹 Работа с удалённым репозиторием (GitHub)

## 🔹 Praca ze zdalnym repozytorium (GitHub)

## 🔹 Working with remote repository (GitHub)

### Добавить удалённый репозиторий

### Dodać repozytorium zdalne

### Add remote repository

```bash
git remote add origin git@github.com:YourUsername/repo-name.git
```

### Проверить удалённые репозитории

### Sprawdzić zdalne repozytoria

### Check remote repositories

```bash
git remote -v
```

### Отправить изменения на GitHub

### Wysłać zmiany na GitHub

### Push changes to GitHub

```bash
git push
```

### Отправить изменения в новую ветку

### Wysłać zmiany do nowej gałęzi

### Push changes to a new branch

```bash
git push -u origin имя_ветки
```

### Скачать изменения с GitHub

### Pobrać zmiany z GitHub

### Pull changes from GitHub

```bash
git pull
```

### Клонировать репозиторий

### Sklonować repozytorium

### Clone a repository

```bash
git clone git@github.com:YourUsername/repo-name.git
```

---

## 🔹 Работа с ветками / Praca z gałęziami / Working with branches

### Посмотреть список веток

### Zobaczyć listę gałęzi

### List branches

```bash
git branch
```

### Создать новую ветку

### Stworzyć nową gałąź

### Create a new branch

```bash
git branch имя_ветки
```

### Создать и сразу перейти в ветку

### Stworzyć i od razu przejść do gałęzi

### Create and switch to branch

```bash
git checkout -b имя_ветки
```

### Переключиться на ветку

### Przełączyć się na gałąź

### Switch to branch

```bash
git checkout имя_ветки
```

### Слить ветку в текущую

### Połączyć gałąź z bieżącą

### Merge branch into current

```bash
git merge имя_ветки
```

### Удалить ветку локально

### Usunąć gałąź lokalnie

### Delete branch locally

```bash
git branch -d имя_ветки
```

---

## 🔹 Полезные команды / Przydatne komendy / Useful commands

### Показать, кто и когда менял строки

### Pokazać, kto i kiedy zmieniał linie

### Show who changed lines and when

```bash
git blame имя_файла
```

### Отменить изменения в файле (до add)

### Cofnąć zmiany w pliku (przed add)

### Discard changes in file (before add)

```bash
git checkout -- имя_файла
```

### Откатить последний коммит (без удаления изменений)

### Cofnąć ostatni commit (z zachowaniem zmian)

### Undo last commit (keep changes)

```bash
git reset --soft HEAD~1
```

### Откатить последний коммит (с удалением изменений)

### Cofnąć ostatni commit (usunąć zmiany)

### Undo last commit (discard changes)

```bash
git reset --hard HEAD~1
```

---

## 🔹 Твой рабочий процесс (для learning-admin)

## 🔹 Twój workflow (dla learning-admin)

## 🔹 Your workflow (for learning-admin)

```bash
# Работа в feature / Praca w feature / Working in feature
git checkout feature
git add .
git commit -m "WIP: working on notes"
git push

# Перенос в dev / Przeniesienie do dev / Move to dev
git checkout dev
git merge feature
git push

# Перенос в main / Przeniesienie do main / Move to main
git checkout main
git merge dev
git push
```

---

**Примечание / Uwaga / Note:**

* `feature` = твоя “кухня” / twoja “kuchnia” / your “kitchen”
* `dev` = рабочая зона / strefa robocza / working area
* `main` = стабильная версия / wersja stabilna / stable version
