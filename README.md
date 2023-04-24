# yamdb_final

![workflow](https://github.com/ya-bessmerti/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)


## Адрес сайта
<<<<<<< HEAD
http://158.160.29.145/redoc/
=======
http://http://158.160.29.145/api/v1/
>>>>>>> dee2b43 (setting)

Проект Yamdb собирает отзывы (Review) пользователей на произведения (Titles).
Работы разделены на категории: «Книги», «Фильмы», «Музыка».
Сами произведения в Yamdb не хранятся; здесь нельзя смотреть кино или слушать музыку.
В каждой категории есть работы: книги, фильмы или музыка.
Произведению может быть присвоен жанр (Жанр) из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»).
Новые жанры может создавать только администратор.
Благодарные или возмущенные пользователи оставляют текстовые отзывы (Review) на работы и оценивают в диапазоне от одного до десяти; рейтинг формируется из оценок пользователей.


## Настройка и запуск сервера в контейнере:

**Клонировать репозиторий**
```bash
git clone https://github.com/p1rt-py/api_yamdb
```
**Перейти в папку:**
```bash
cd infra
```
**Развернуть контейнеры:**
```bash
docker-compose up -d --build 
```

**Сделать миграции, суперпользователя и собрать статику:**
```bash
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser
docker-compose exec web python manage.py collectstatic --no-input
```

**Заполнить базу данными из копии:**
```bash
docker-compose exec web python manage.py loaddata ../infra/fixtures.json 
```


## Технологии:
Python 3.8
Django 2.2.28
Djangorestframework 3.12.4
Redoc_

## Документация и примеры использования API:
Доступны по GET-запросу на эндпойнт /redoc/
