# notification service


### Используется
- [x] swagger


## Get started


### ◦ Виртуальное окружение

Создайте виртуальное окружение. 

```commandline
python -m venv venv
```

> Здесь используется утилита "venv" для создания виртуального окружения, но вы в праве использовать любой другой инструмент.


### ◦ Переменные окружения

В данном проекте вам необходимо использовать переменные окружения. Это данные, которые вы записываете в файл .env, чтобы скрыть информацию от ненужных глаз. 

Скопируйте содержимое .env.example и подставьте нужные значения.

```commandline
cp .env.example .env
```

## База
В качестве базы используется Postgresql. Так что, перед запуском пректа нужно создать базу.


## Запуск через докер

В данном проекте вы можете запустить проект через докер.

```commandline
docker-compose build
docker run --rm web python manage.py makemigrations
docker run --rm web python manage.py migrate
docker run --rm web python manage.py createsuperuser
```

Затем запустите проект через докер композ

```commandline
docker-compose up
```

## Запуск локально

После создания виртуального окружения вам необходимо установить зависимости.
Вы можете это сделать посредством poetry или же напрямую через pip install.
Но для начала желательно обновить пакет пип

```commandline
python -m pip install --upgrade pip
```

Зате вы можете использовать один из двух вариантов установки зависимостей

### pip

```commandline
python -m pip install -r requirements.txt
```

### poetry

```commandline
python -m pip install poetry
poetry install
```


После установки зависимостей вам необходимо мигрировать данные и после создать супер юзера.


```commandline
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser
```

Потом запустить приложение django, celery и redis паралельно

```commandline
redis-server
python -m celery -A config worker -l info
python manage.py runserver
```

### 