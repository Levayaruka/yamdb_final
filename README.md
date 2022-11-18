### Адрес
http://130.193.51.9/redoc
# yamdb_final
![example workflow](https://github.com/levayaruka/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)
### Описание
CI/CD и docker-compose к проекту раннему api_yamdb
### Запуск проекта в dev-режиме
- В директории infra создайте файл .env и заполните по образцу
```
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432 
```
- В директроии infra_sp2/infra выполните команду по запуску docker-compose ```docker-compose up --build -d```
- Далее выполните миграции, загрузите статику и создайте администратора
```
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py collectstatic
docker-compose exec web python manage.py createsuperuser
```
- После перезапустите docker-compose 
```
docker-compose down -v
docker-compose up --build -d
```