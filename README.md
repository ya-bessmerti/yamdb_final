# yamdb_final

![workflow](https://github.com/ya-bessmerti/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

Проект Yamdb собирает отзывы (Review) пользователей на произведения (Titles).
Работы разделены на категории: «Книги», «Фильмы», «Музыка».
Сами произведения в Yamdb не хранятся; здесь нельзя смотреть кино или слушать музыку.
В каждой категории есть работы: книги, фильмы или музыка.
Произведению может быть присвоен жанр (Жанр) из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»).
Новые жанры может создавать только администратор.
Благодарные или возмущенные пользователи оставляют текстовые отзывы (Review) на работы и оценивают в диапазоне от одного до десяти; рейтинг формируется из оценок пользователей.

## Адрес сайта
http://158.160.29.145/api/v1/

## Документация:
http://158.160.29.145/redoc/

## Технологии:
Python 3.8
Django 3.2
Djangorestframework 3.12.4
Redoc_


## Как запустить проект:
- Клонируйте репозиторий `github.com/ya-bessmerti/yamdb_final.git`

- Скопируйте файлы `docker-compose.yaml` и `nginx/default.conf` из проекта в папке _**infra**_ на сервер в `home/<ваш_username>/docker-compose.yaml` и `home/<ваш_username>/nginx/default.conf` соответственно.

- Установите docker:
    ```bash
    sudo apt install docker.io 
    ```
- Установите docker-compose, с этим вам поможет [официальная документация](https://docs.docker.com/compose/install/).
- Заполните Secrets Actions по шаблону наполнения env переменных в GitHub Actions
    ```
    Наименование:        Содержание:
    DB_ENGINE            django.db.backends.postgresql # указываем, что работаем с postgresql
    DB_NAME              postgres # имя базы данных
    POSTGRES_USER        postgres # логин для подключения к базе данных
    POSTGRES_PASSWORD    postgres # пароль для подключения к БД (установите свой)
    DB_HOST              db # название сервиса (контейнера)
    DB_PORT              5432 # порт для подключения к БД 
    HOST                 ..... # ip сервера
    USER                 MrGorkiy # UserName для подключению к серверу
    SSH_KEY              # Приватный ключ доступа для подключению к серверу `cat ~/.ssh/id_rsa`
    PASSPHRASE           # Серкретный ключ\фраза, если ваш ssh-ключ защищён фразой-паролем
    TELEGRAM_TO          # id чата пользователя или чата куда бот будет отправлять результат успешного выполнения
    TELEGRAM_TOKEN       # Токен бота ТГ для отправки уведомления
    DOCKER_USERNAME      # Имя пользователя Docker для публикации образов
    DOCKER_PASSWORD      # Пароль пользоывателя Docker
    ```
- Сделайте коммит в ветку Master/Main и готовый проект развернется у вас на сервере

- Сделать миграции, суперпользователя и собрать статику:**
```bash
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser
docker-compose exec web python manage.py collectstatic --no-input
```
