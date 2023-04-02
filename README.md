# API_YMDB
## _Проект для обмена данными с сервисом Yamdb через API_
## Описание:
Проект YaMDb собирает отзывы пользователей на произведения. Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку. Произведения делятся на категории, такие как «Книги», «Фильмы», «Музыка».
Пользователи могут оставлять к произведениям текстовые отзывы и ставят произведению оценку в диапазоне от одного до десяти (целое число)
Запросы к API начинаются с
```sh
/api/v1/
```
## Установка:
1. Клонируйте репозиторий, перейдите в него:
```sh
git clone git@github.com:Praskovya39/infra_sp2.git
cd api_yamdb
```
2. Создайте и откройте файл ```.env``` с переменными оккружения:
```sh
cd infra
touch .env
```
3. Заполните ```.env``` файл, к примеру вот так:
```sh
DB_ENGINE=django.db.backends.postgresql <указываем, что работаем с postgresql>
DB_NAME=<имя базы данных>
POSTGRES_USER=<логин для подключения к базе данных>
POSTGRES_PASSWORD=<пароль для подключения к БД (установите свой)>
DB_HOST=<название сервиса (контейнера)>
DB_PORT=<порт для подключения к БД>
```

4. Установка и запуск приложения (Загрузив контейнер web из DockerHub):
```sh
docker-compose up -d
```
5. Примените миграции, создайте суперпользователя, сбор статики и заполните БД:
```sh
docker-compose exec web python manage.py migrate

docker-compose exec web python manage.py createsuperuser

docker-compose exec web python manage.py collectstatic --no-input 

docker-compose exec web python manage.py loaddata fixtures.json
```

## Документация:
Более подробно с возможностями API можно ознакомиться в документации по адресу (После запуска проекта): 
```sh
http://127.0.0.1:8000/redoc/
```
