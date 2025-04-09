# Git-Helper

Это проект-помощник служит руководством для работы с Git, системой контроля версий. Он содержит основные команды, понятия и инструкции по инициализации проекта, работе с коммитами и регистрации на GitHub.

## Основные понятия

- **Репозиторий**: Хранилище для вашего проекта, которое содержит все файлы и историю изменений.
- **Коммит**: Снимок состояния вашего репозитория в определённый момент времени, сохраняющий изменения.
- **Ветка**: Независимая линия разработки в репозитории. Основная ветка обычно называется `main` или `master`.
- **Слияние (Merge)**: Процесс объединения изменений из одной ветки в другую.
- **Удалённый репозиторий**: Репозиторий, размещённый на сервере, например, на GitHub, GitLab или Bitbucket.

## Установка Git

1. **Windows**: Скачайте и установите [Git для Windows](https://git-scm.com/download/win).
2. **macOS**: Установите через Homebrew:

```bash
   brew install git
```

3. **Linux**: Установите через пакетный менеджер вашего дистрибутива:

```bash
   sudo apt-get install git  # для Ubuntu
   sudo dnf install git      # для Fedora
```


## Инициализация проекта

Для инициализации нового проекта выполните следующие шаги:

1. Создайте новую папку для вашего проекта и перейдите в неё:

```bash
   mkdir my-project
   cd my-project
```

2. Инициализируйте новый репозиторий:

```bash
   git init
```

**Теперь у вас есть пустой репозиторий Git, готовый к работе!**

## Работа с коммитами

1. **Добавьте файлы в репозиторий**:
   Для добавления всех файлов используйте:

```bash
   git add .
```

Или добавьте конкретный файл:

```bash
   git add filename.txt
```
   
2. **Создайте коммит**:
   После добавления файлов создайте коммит, описав изменения:

```bash
   git commit -m "Добавлено первое описание"
```

3. **Посмотрите историю коммитов**:
   Чтобы просмотреть историю изменений:

```bash
   git log
```

## Работа с ветками

1. **Создайте новую ветку**:

```bash
   git branch new-branch
```
   
2. **Переключитесь на новую ветку**:

```bash
   git checkout new-branch
```

3. **Объедините ветку с основной**:
   Перейдите на основную ветку и объедините изменения:

```bash
   git checkout main
   git merge new-branch
```

## Регистрация на GitHub

1. Перейдите на [GitHub](https://github.com/) и нажмите "Sign up".
2. Введите свою электронную почту, создайте пароль и введите ваше имя пользователя.
3. Следуйте инструкциям для подтверждения регистрации.

## Создание удалённого репозитория на GitHub

1. Войдите в свой аккаунт на GitHub.
2. Нажмите на кнопку "New" или "Create repository".
3. Введите имя репозитория и описание.
4. Выберите опции по умолчанию и нажмите "Create repository".

Теперь ваш удалённый репозиторий создан. Чтобы связать локальный репозиторий с удалённым, выполните следующие команды:

```bash
git remote add origin https://github.com/username/my-project.git
git branch -M main
git push -u origin main
```

## Полезные команды Git

- `git status`: Просмотреть статус файла в репозитории.
- `git clone <url>`: Клонировать удалённый репозиторий.
- `git pull`: Получить последние изменения из удалённого репозитория.
- `git push`: Отправить ваши коммиты на удалённый репозиторий.

# Хеш, лог и HEAD в commit

Три важных понятия, которые необходимо знать при работе с Git:

- **Хеш** - идентификатор коммита.
- **Лог** - список коммитов с их описанием.
- **HEAD** - последний сделанный коммит.

Команда `git log` выводит информацию о коммитах, включая строчки с набором букв и цифр. Информация о коммите — это набор данных: когда был сделан коммит, содержимое файлов в репозитории на момент коммита и ссылка на предыдущий, или родительский, коммит. Git хеширует (преобразует) эту информацию с помощью алгоритма SHA-1 и получает для каждого коммита свой уникальный хеш — результат хеширования.

Хеширование (от англ. hash, «рубить», «крошить», «мешанина») — это способ преобразовать набор данных и получить их «отпечаток». Информация относительно коротка (40 символов в случае SHA-1) и состоит из цифр 0 — 9 и латинских букв A — F (неважно, заглавных или строчных). Хеш обладает следующими важными свойствами:

- Если хеш получить дважды для одного и того же набора входных данных, то результат будет гарантированно одинаковый.
- Если хоть что-то в исходных данных поменяется (хотя бы один символ), то хеш тоже изменится (причём сильно).

Элементы, состоящие в описании лог

- **Строка из цифр и латинских букв** после слова `commit` — это уже знакомый вам хеш коммита.
- **Author** — имя автора и его электронная почта.
- **Date** — дата и время создания коммита.
- **Сообщение к коммиту.**

Если в репозитории уже много коммитов, необходимо вызвать сокращённый лог командой `git log` с флагом `--oneline`. При этом в терминале появятся только первые несколько символов хеша каждого коммита и комментарии к ним.

Сокращённый хеш (первые несколько символов полного) можно использовать точно так же, как и полный. Для этого команда `git log --oneline` автоматически подбирает такую длину сокращённых хешей, чтобы они были уникальными в пределах репозитория и Git всегда мог понять, о каком коммите идёт речь.

При вызове команды `git log` также присутствует надпись `(HEAD -> master)` после хеша одного из коммитов.

Файл `HEAD` (англ. «голова», «головной») — один из служебных файлов папки `.git`. Он указывает на коммит, который сделан последним (то есть на самый новый).

Если нужно передать последний коммит, то вместо его хеша можно просто написать слово `HEAD` — Git поймёт, что имелось в виду последний коммит.

## Заключение

Git — это мощная система контроля версий, которая помогает организовать и отслеживать изменения в ваших проектах. Надеемся, что данный помощник будет полезен для вас при работе с Git!

Для получения дополнительной информации и ресурсов, пожалуйста, посетите [официальную документацию Git](https://git-scm.com/doc).

