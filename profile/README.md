## Hi there 👋

# Git & GitHub Шпаргалка для командной работы

## 0. Git-Flow базовые правила
- Основная ветка: `main` — стабильный продакшн-код.
- Разработка новых функций: ветки `feature/имя-фичи`.
- Исправления ошибок: ветки `fix/описание-исправления`.
- Критические исправления в продакшне: ветки `hotfix/краткое-описание`.
- Релизные ветки (по желанию): `release/x.y.z` для подготовки к релизу.
- Ветки создаются от `main` или от релизной ветки.
- После завершения работы ветки сливаются через Pull Request в `main` или релизную ветку.

## 1. Клонирование и форк
1. **Клонирование репозитория**
```bash
git clone https://github.com/username/repository.git
cd repository
````

* Клонирует репозиторий на ваш компьютер и создаёт локальную копию с подключённым удалённым репозиторием `origin`.

2. **Настройка upstream (для форка)**

```bash
git remote add upstream https://github.com/original-owner/repository.git
git fetch upstream
git checkout main
git merge upstream/main
```

* `git remote add upstream <URL>` — добавляет новый удалённый репозиторий с именем `upstream`.

  * Используется, если вы работаете с форком, чтобы синхронизировать изменения с оригинальным репозиторием.
  * `origin` — ваш форк (или основной репозиторий), `upstream` — оригинальный репозиторий, от которого вы форкнули.
* `git fetch upstream` — подтягивает все изменения из оригинального репозитория, не сливая их с вашей веткой.
* `git checkout main` — переключение на локальную основную ветку.
* `git merge upstream/main` — сливает последние изменения из оригинального репозитория в вашу локальную ветку `main`.

## 2. Ветки

* `main` — стабильная версия.
* Ветки для фич и исправлений:

```
feature/имя-фичи
fix/описание-исправления
hotfix/критическая-поправка
```

* Создание новой ветки:

```bash
git checkout -b feature/my-feature
```

* Обновление ветки `main`:

```bash
git checkout main
git pull origin main
```

## 3. Работа с кодом

* Добавление и коммит изменений:

```bash
git add .
git commit -m "Краткое описание изменений"
```

* Подтягивание изменений из main:

```bash
git checkout main
git pull origin main
git checkout feature/my-feature
git rebase main
# или merge
git merge main
```

## 4. Пуш ветки и Pull Request

* Пуш ветки на GitHub:

```bash
git push origin feature/my-feature
```

* Создание PR:

  * base: main, compare: feature/my-feature
  * Добавить описание изменений
  * Указать ревьюеров (@username)

## 5. Ревью и исправления

* Вносить исправления после ревью:

```bash
git add .
git commit -m "Исправления по ревью"
git push origin feature/my-feature
```

* PR автоматически обновится

## 6. Слияние PR

* Merge commit — сохраняет историю
* Squash and merge — объединяет все коммиты в один
* Rebase and merge — добавляет коммиты ветки поверх main

## 7. Удаление ветки

* Локально:

```bash
git branch -d feature/my-feature
```

* На GitHub: кнопка Delete branch после слияния PR

## 8. Полезные команды

* Просмотр веток:

```bash
git branch           # локальные
git branch -r        # удаленные
git branch -a        # все
```

* Просмотр изменений:

```bash
git status
git diff
git log --oneline
```

* Отмена изменений:

```bash
git checkout -- <file>      # отменить локальные изменения файла
git reset HEAD <file>       # убрать из staging
git revert <commit>         # отменить коммит
```

* Работа с удаленным репозиторием:

```bash
git fetch origin
git pull origin main
git push origin feature/my-feature
```

* Слияние веток:

```bash
git merge <branch>
git rebase <branch>
```

* Стягивание изменений с upstream (для форка):

```bash
git fetch upstream
git checkout main
git merge upstream/main
```

## 9. Рекомендации

* Делать мелкие коммиты с понятными сообщениями
* Обновлять ветку из main перед PR
* Описывать PR понятно
* Использовать Labels / Projects / Milestones для задач

```

