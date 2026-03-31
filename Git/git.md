# 📘 Git: Краткая сводка для справки

## 1. Что такое Git?

**Git** — распределенная система контроля версий, позволяющая:
- Отслеживать изменения в коде
- Работать в команде
- Создавать ветки для новых функций
- Откатываться к предыдущим версиям
- Сохранять историю разработки

---

## 2. Основные команды

### 2.1. Настройка

```bash
# Установка имени пользователя
git config --global user.name "Имя Фамилия"
git config --global user.email "email@example.com"

# Настройка редактора
git config --global core.editor "code --wait"

# Просмотр настроек
git config --list

# Цветной вывод
git config --global color.ui auto
```

### 2.2. Создание и клонирование репозитория

```bash
# Инициализация нового репозитория
git init

# Клонирование существующего репозитория
git clone https://github.com/user/repo.git
git clone git@github.com:user/repo.git  # SSH

# Клонирование в конкретную папку
git clone https://github.com/user/repo.git my-folder

# Клонирование конкретной ветки
git clone -b develop https://github.com/user/repo.git
```

---

## 3. Работа с изменениями

### 3.1. Базовые команды

```bash
# Проверка статуса
git status
git status -s  # Короткий формат

# Добавление файлов в staging
git add file.txt           # Один файл
git add .                  # Все файлы
git add *.js               # Все js файлы
git add -A                 # Все изменения (включая удаленные)

# Удаление из staging
git reset file.txt         # Убрать из staging
git reset                  # Убрать всё из staging

# Коммит
git commit -m "Сообщение коммита"
git commit -am "Сообщение" # Добавить и закоммитить (только отслеживаемые)

# Просмотр изменений
git diff                   # Не добавленные в staging
git diff --staged          # Добавленные в staging
git diff HEAD              # Все изменения
git diff branch1..branch2  # Разница между ветками
```

### 3.2. История

```bash
# Просмотр истории
git log
git log --oneline          # Компактный вид
git log --graph            # Графическое отображение
git log --oneline --graph  # Комбинация
git log -n 5               # Последние 5 коммитов

# Просмотр изменений в коммите
git show commit_hash
git show HEAD              # Последний коммит
git show HEAD~1            # Предпоследний коммит
```

### 3.3. Отмена изменений

```bash
# Отмена незакоммиченных изменений
git checkout -- file.txt   # Отменить изменения в файле
git restore file.txt       # Альтернативный синтаксис
git reset --hard HEAD      # Отменить все незакоммиченные изменения

# Отмена коммита
git reset --soft HEAD~1    # Отменить коммит, оставить изменения
git reset --hard HEAD~1    # Полностью удалить последний коммит
git revert commit_hash     # Создать коммит, отменяющий изменения

# Возврат к конкретному коммиту
git checkout commit_hash   # Временный просмотр
git reset --hard commit_hash # Безвозвратное изменение
```

---

## 4. Работа с ветками

### 4.1. Управление ветками

```bash
# Просмотр веток
git branch                 # Локальные
git branch -r              # Удаленные
git branch -a              # Все ветки

# Создание ветки
git branch feature/new-feature
git checkout -b feature/new-feature  # Создать и переключиться

# Переключение между ветками
git checkout main
git switch main            # Альтернативный синтаксис

# Удаление ветки
git branch -d feature/old  # Безопасное удаление
git branch -D feature/old  # Принудительное удаление

# Переименование ветки
git branch -m old-name new-name
```

### 4.2. Слияние веток

```bash
# Слияние ветки в текущую
git merge feature/new-feature

# Слияние с сохранением истории (rebase)
git checkout feature
git rebase main
git checkout main
git merge feature

# Прерывание конфликтного слияния
git merge --abort

# Продолжение после разрешения конфликтов
git add .
git commit -m "Merge conflicts resolved"
```

### 4.3. Управление конфликтами

```bash
# При конфликте:
# 1. Открыть файлы с конфликтами (<<<<<<<, =======, >>>>>>>)
# 2. Вручную разрешить конфликт
# 3. Добавить исправленные файлы
git add file.txt

# 4. Продолжить слияние
git commit -m "Merge: resolved conflicts"

# Инструменты для разрешения конфликтов
git mergetool  # Открывает визуальный инструмент
```

---

## 5. Работа с удаленными репозиториями

### 5.1. Управление удаленными репозиториями

```bash
# Просмотр удаленных репозиториев
git remote -v

# Добавление удаленного репозитория
git remote add origin https://github.com/user/repo.git
git remote add upstream https://github.com/original/repo.git

# Изменение URL
git remote set-url origin https://github.com/user/repo.git

# Удаление удаленного репозитория
git remote remove upstream
```

### 5.2. Отправка и получение изменений

```bash
# Получение изменений
git fetch                 # Получить, но не сливать
git fetch origin          # Получить из конкретного репозитория
git pull                  # fetch + merge
git pull --rebase         # fetch + rebase

# Отправка изменений
git push origin main      # Отправить ветку
git push -u origin feature # Отправить и установить upstream
git push origin --delete feature # Удалить ветку на сервере
git push --tags           # Отправить теги

# Принудительная отправка (осторожно!)
git push --force origin main
git push --force-with-lease origin main  # Безопаснее
```

---

## 6. Теги

```bash
# Просмотр тегов
git tag
git tag -l "v1.*"          # Поиск по шаблону

# Создание тегов
git tag v1.0.0             # Легкий тег
git tag -a v1.0.0 -m "Release version 1.0.0"  # Аннотированный

# Отправка тегов
git push origin v1.0.0
git push --tags            # Все теги

# Удаление тегов
git tag -d v1.0.0          # Локально
git push origin --delete v1.0.0  # Удаленно

# Переключение на тег
git checkout v1.0.0
```

---

## 7. Stash (Временное хранение)

```bash
# Сохранение незакоммиченных изменений
git stash
git stash save "Сообщение"

# Просмотр stash
git stash list
git stash show stash@{0}

# Восстановление
git stash pop              # Восстановить и удалить из stash
git stash apply            # Восстановить, оставить в stash
git stash apply stash@{1}  # Конкретный stash

# Удаление
git stash drop             # Удалить последний
git stash drop stash@{0}   # Удалить конкретный
git stash clear            # Удалить все

# Создание ветки из stash
git stash branch new-branch stash@{0}
```

---

## 8. Полезные команды

### 8.1. Поиск

```bash
# Поиск по коммитам
git log --grep="фикс"

# Поиск по содержимому
git grep "functionName"
git grep -n "search"        # С номерами строк

# Поиск кто изменил строки
git blame file.txt
git blame -L 10,20 file.txt # Конкретные строки
```

### 8.2. Очистка

```bash
# Очистка неотслеживаемых файлов
git clean -n               # Показать что будет удалено
git clean -f               # Удалить
git clean -fd              # Удалить включая папки
git clean -fx              # Удалить включая .gitignore

# Оптимизация репозитория
git gc
git fsck                   # Проверка целостности
```

### 8.3. Алиасы

```bash
# Создание алиасов
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.st status
git config --global alias.lg "log --oneline --graph --all"

# Использование
git co main
git br feature
git st
git lg
```

---

## 9. .gitignore

```gitignore
# Зависимости
node_modules/
/vendor/

# Файлы окружения
.env
.env.local
.env.*.local

# Логи
*.log
npm-debug.log*
yarn-debug.log*

# Системные файлы
.DS_Store
Thumbs.db

# IDE
.vscode/
.idea/
*.swp
*.swo

# Сборка
/dist/
/build/
*.min.js

# Покрытие тестов
/coverage/

# Временные файлы
*.tmp
*.temp
```

---

## 10. Git Flow (Рабочий процесс)

### 10.1. Основные ветки

```
main (master)     # Продакшн, всегда стабильная
develop           # Разработка, интеграция
feature/*         # Новые функции
release/*         # Подготовка к релизу
hotfix/*          # Срочные исправления
```

### 10.2. Стандартные команды

```bash
# Начало разработки
git checkout develop
git pull origin develop
git checkout -b feature/new-feature

# Завершение фичи
git checkout develop
git pull origin develop
git merge --no-ff feature/new-feature
git push origin develop
git branch -d feature/new-feature

# Создание релиза
git checkout -b release/1.0.0 develop
# ... подготовка ...
git checkout main
git merge --no-ff release/1.0.0
git tag -a v1.0.0 -m "Release 1.0.0"
git checkout develop
git merge --no-ff release/1.0.0
git branch -d release/1.0.0

# Hotfix
git checkout -b hotfix/1.0.1 main
# ... исправление ...
git checkout main
git merge --no-ff hotfix/1.0.1
git tag -a v1.0.1 -m "Hotfix 1.0.1"
git checkout develop
git merge --no-ff hotfix/1.0.1
git branch -d hotfix/1.0.1
```

---

## 11. Соглашения по коммитам (Conventional Commits)

### 11.1. Формат

```
<type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

### 11.2. Типы коммитов

| Тип | Описание |
|-----|----------|
| `feat` | Новая функциональность |
| `fix` | Исправление бага |
| `docs` | Изменения в документации |
| `style` | Форматирование, стили (не влияет на код) |
| `refactor` | Рефакторинг |
| `perf` | Улучшение производительности |
| `test` | Добавление тестов |
| `chore` | Обслуживание, сборка |
| `ci` | Изменения CI/CD |
| `build` | Изменения сборки |

### 11.3. Примеры

```bash
# Простой коммит
feat(auth): add login with Google

# С описанием
fix(api): handle null response from user service

The user service sometimes returns null when user
is not found. This fix adds proper error handling.

Closes #123

# Breaking change
feat!: remove deprecated API endpoints

BREAKING CHANGE: API v1 endpoints removed, use v2

# Несколько типов
docs: update README
chore: add pre-commit hooks
```

---

## 12. Работа с Submodules

```bash
# Добавление подмодуля
git submodule add https://github.com/user/lib.git libs/lib

# Инициализация подмодулей
git submodule init
git submodule update

# Клонирование с подмодулями
git clone --recursive https://github.com/user/repo.git

# Обновление подмодулей
git submodule update --remote

# Удаление подмодуля
git submodule deinit libs/lib
git rm libs/lib
```

---

## 13. Решение проблем

### 13.1. Отмена последнего коммита

```bash
# Мягкая отмена (изменения остаются)
git reset --soft HEAD~1

# Жесткая отмена (изменения удаляются)
git reset --hard HEAD~1
```

### 13.2. Исправление последнего коммита

```bash
# Добавить файлы в последний коммит
git add forgotten-file.txt
git commit --amend -m "Новое сообщение"

# Только изменить сообщение
git commit --amend
```

### 13.3. Восстановление удаленного коммита

```bash
# Найти удаленный коммит
git reflog
# Вернуться к нему
git checkout HEAD@{2}
# Создать ветку
git branch recover-branch
```

### 13.4. Обновление fork

```bash
# Добавить upstream
git remote add upstream https://github.com/original/repo.git

# Получить изменения
git fetch upstream

# Обновить main
git checkout main
git merge upstream/main

# Обновить ветку
git checkout feature
git rebase main
```

---

## 14. Полезные команды для командной работы

```bash
# Просмотр авторов
git shortlog -s -n

# Кто что делал
git log --author="Имя"

# Статистика изменений
git log --stat
git diff --shortstat

# Поиск коммита по сообщению
git log --grep="fix"

# Поиск изменений в файле
git log -p file.txt

# Просмотр незапушенных коммитов
git log origin/main..HEAD

# Список измененных файлов между коммитами
git diff --name-only commit1 commit2
```

---

## 15. Интеграция с GitHub/GitLab

```bash
# Создание PR через командную строку (GitHub CLI)
gh pr create --title "Feature" --body "Description"

# Создание репозитория на GitHub
gh repo create my-repo --public --source=. --remote=origin --push

# Открытие репозитория в браузере
git remote show origin
# или
gh repo view --web
```

---

## 16. Рекомендации

### 16.1. Правила хорошего тона

```bash
# ✅ Часто коммитить маленькими порциями
# ✅ Писать понятные сообщения коммитов
# ✅ Не коммитить секреты и конфиги
# ✅ Делать rebase перед push
# ✅ Использовать .gitignore
# ✅ Пушить перед уходом
```

### 16.2. Чего избегать

```bash
# ❌ git push --force на общую ветку
# ❌ Коммитить бинарные файлы
# ❌ Долго не пушить
# ❌ Коммитить нерабочий код в main
# ❌ Игнорировать конфликты
```

---

## 17. Шпаргалка быстрых команд

| Команда | Описание |
|---------|----------|
| `git init` | Создать репозиторий |
| `git clone <url>` | Склонировать репозиторий |
| `git add .` | Добавить все изменения |
| `git commit -m "msg"` | Создать коммит |
| `git push` | Отправить изменения |
| `git pull` | Получить изменения |
| `git branch` | Показать ветки |
| `git checkout -b <name>` | Создать ветку |
| `git merge <branch>` | Слить ветку |
| `git status` | Проверить статус |
| `git log --oneline` | Показать историю |
| `git reset --hard HEAD~1` | Отменить последний коммит |
| `git stash` | Спрятать изменения |
| `git diff` | Показать изменения |

---

## 18. Полезные ссылки

- [Официальная документация Git](https://git-scm.com/doc)
- [GitHub Docs](https://docs.github.com/ru)
- [Git Flight Rules](https://github.com/k88hudson/git-flight-rules)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Git Flow Cheatsheet](https://danielkummer.github.io/git-flow-cheatsheet/)

---

Эта сводка покрывает основные команды и концепции Git для ежедневной работы. Для глубокого изучения рекомендуется обратиться к официальной документации и практиковаться в работе с репозиториями.
