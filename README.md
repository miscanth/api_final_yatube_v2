![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)  ![Django](https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=django&logoColor=white)


## API для Социальной сети
Сама социальная сеть - это платформа для публикации личных дневников, написанная на **Django**.
Она даёт пользователям возможность создать учетную запись, публиковать записи, подписываться на понравившихся авторов и оставлять комментарии к постам.

Данный проект - это API социальной сети - написан с использованием библиотеки **Django REST Framework**.
В проекте используются **JWT-токены** для аутентификации. Работа с JWT-токенами организована при помощи библиотеки **Djoser**.
В проекте реализован поиск по подпискам по параметру search с помощью встроенного бэкенда **SearchFilter**, который идёт в составе библиотеки **filters**.


### Технологии
- Python 3.9
- Django 2.2.16
- Django REST Framework 3.12.4
- Django REST framework simple JWT  4.7.2


### Как запустить проект:
Клонировать репозиторий и перейти в него в командной строке:
```
git clone https://github.com/miscanth/api_final_yatube_v2.git
```
```
cd api_final_yatube_v2
```
Cоздать и активировать виртуальное окружение:
```
python3 -m venv venv
```
```
source venv/bin/activate
```
Установить зависимости из файла requirements.txt:
```
python3 -m pip install --upgrade pip
```
```
pip install -r requirements.txt
```
Выполнить миграции:
```
python3 manage.py migrate
```
Запустить проект:
```
python3 manage.py runserver
```

### Примеры запросов:
Пример POST-запроса с токеном пользователя Martr: добавление нового поста.
*POST .../api/v1/posts/*
```
{
    "text": "Здравствуйте, я ваша Тётя!"
    "group": "1"
}
```
Пример ответа:
```
{
    "id": 1,
    "author": "Martr",
    "text": "Здравствуйте, я ваша Тётя!",
    "pub_date": "2023-05-06T16:43:04.502523Z",
    "image": null,
    "group": 1
}
```
Пример POST-запроса с токеном пользователя Dorka: добавление нового комментария к посту другого пользователя.
*POST .../api/v1/posts/1/comments/*
```
{
    "text": "я очень люблю трогательную музыку. Сыграйте нам военный марш, да погромче!"
}
```
Пример ответа:
```
{
    "id": 1,
    "author": "Dorka",
    "text": "я очень люблю трогательную музыку. Сыграйте нам военный марш, да погромче!",
    "created": "2023-05-06T16:58:23.071217Z",
    "post": 1
}
```
Пример POST-запроса с токеном пользователя Dorka: Подписка пользователя от имени которого сделан запрос на пользователя переданного в теле запроса.
*POST .../api/v1/follow/*
```
{
    "following": "Martr"
}
```
Пример ответа:
```
{
    "id": 1,
    "user": "Dorka",
    "following": "Martr",
    "pub_date": "2023-05-06T17:01:12.264202Z"
}
```


## Разработчик (исполнитель):
👩🏼‍💻 Юлия: https://github.com/miscanth