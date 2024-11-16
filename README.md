![yamdb workflow](https://github.com/Tox1que/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)


# Описание сервиса:
### *Как Кинопоиск, только хуже :)*
### API для сервиса, который собирает отзывы на произведения искусства:
- Кино
- Музыка
- Книги


## Возможности:
- Создание аккаунта пользователя
- Публикация, изменение, удаления отзывов к произведениям
- Публикация, изменение, удаления комментариев к отзывам
- Реализованы поиск и фильтрация в запросах

## Технологии
[![Python](https://img.shields.io/badge/Python-3776AB?logo=python)](https://www.python.org/)
[![Django](https://img.shields.io/badge/Django-092E20?&logo=django)](https://www.djangoproject.com/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-grey?logo=postgresql)](https://www.postgresql.org/)
[![Django REST Framework](https://img.shields.io/badge/Django_REST_Framework-grey?logo=django)](https://www.django-rest-framework.org/)
[![JSON Web Tokens](https://img.shields.io/badge/JSON_Web_Tokens-grey?logo=jsonwebtokens)](https://jwt.io/)
[![Gunicorn](https://img.shields.io/badge/Gunicorn-grey?logo=gunicorn)](https://gunicorn.org/)
[![nginx](https://img.shields.io/badge/nginx-grey?logo=nginx)](https://nginx.org/)
[![Docker](https://img.shields.io/badge/Docker-grey?logo=docker)](https://www.docker.com/)
[![Docker Compose](https://img.shields.io/badge/Docker_Compose-grey?logo=docker)](https://docs.docker.com/compose/)
[![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-grey?logo=githubactions)](https://github.com/features/actions)

## Как запустить проект на удалённом сервере:
Добавьте в Secrets GitHub Actions следующие переменные окружения:
```
USER=<имя пользователя для подключения к серверу>
HOST=<IP-адрес вашего сервера>
SSH_KEY=<приватный ключ с компьютера, имеющего доступ к боевому серверу>
PASSPHRASE=<Если при создании ssh-ключа вы использовали фразу-пароль>
SECRET_KEY=<секретный ключ проекта>
ALLOWED_HOSTS=<список хостов (указывать через пробел)>
DB_ENGINE=<тип базы данных>
DB_NAME=<имя базы данных>
POSTGRES_USER=<логин для подключения к базе данных>
POSTGRES_PASSWORD=<пароль для подключения к БД>
DB_HOST=<название сервиса (контейнера)>
DB_PORT=<порт для подключения к БД>
DOCKER_USERNAME=< DockerHub имя пользователя>
DOCKER_PASSWORD=<DockerHub пароль>
TELEGRAM_TO=<ID вашего телеграм-аккаунта>
TELEGRAM_TOKEN=<токен вашего бота>
```
Установите docker:
```
sudo apt install docker.io
```
Установите docker-compose, в этом вам поможет [официальная документация](https://docs.docker.com/compose/install/).

Скопируйте подготовленные файлы docker-compose.yaml и nginx/default.conf из вашего проекта на сервер в home/<ваш_username>/docker-compose.yaml и home/<ваш_username>/nginx/default.conf соответственно. 

При пуше в ветку main код автоматически деплоится на сервер.

Создайте и примените миграции:
```
sudo docker-compose exec web python manage.py makemigrations
sudo docker-compose exec web python manage.py migrate --noinput
```
Соберите статику:
```
sudo docker-compose exec web python manage.py collectstatic --no-input
```
