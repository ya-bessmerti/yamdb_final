# yamdb_final
![workflow](https://github.com/ya-bessmerti/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg?branch=master&event=push)

![Logo](https://cdn-irec.r-99.com/sites/default/files/product-images/399872/EOXOqQkXnjTMTRnIpMUSvQ.jpg)




### Настройка и запуск сервера в контейнере:

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


### Технологии:
Python 3.8
Django 2.2.28
Djangorestframework 3.12.4
Redoc_

### Документация и примеры использования API:
Доступны по GET-запросу на эндпойнт /redoc/