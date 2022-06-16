# api_final_yatube
***

**api_final_yatube** представляет собой проект API сервиса социальной сети в которой реализованы возможности:
публикации записи, оставления комментариев к записям, а так же реализован механизм подписки или отписки на авторов.

Проект предназначен для закрепления полученых знаний и навыков работы с **Django REST framework**.

***

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/SKhnykin/api_final_yatube.git
```

```
cd yatube_api
```

Cоздать и активировать виртуальное окружение:

```
python -m venv env
```

Для *nix-систем:

```
source venv/bin/activate
```

Для windows-систем:

``` 
source venv\Scripts\activate
```

Установить зависимости из файла requirements.txt:

```
pip install -r requirements.txt
```

Выполнить миграции:

```
python manage.py migrate
```

Запустить проект:

```
python manage.py runserver
```

***
### Некоторые примеры запросов к API:
***

**Получение списка сообществ:**

эндпойнт:

```
/api/v1/groups/
```

разрешённые HTTP-методы:

```
GET
```

в ответе:

```
[
  {
    "id": 0,
    "title": "string",
    "slug": "string",
    "description": "string"
  }
]
```

response status code:

```
200
```


**Создание подписки**

эндпойнт:

```
/api/v1/follow/
```

http-метод:

```
POST
```

Payload:

```
{
  "following": "string"
}
```

**Варианты ответов:**
* удачное выполнение - статус 201 и созданный экземпляр подписки

```
{
  "user": "string",
  "following": "string"
}
```

* отклонение запроса - статус 400 - пропущен обязательный параметр

```
{
  "following": [
    "Обязательное поле."
  ]
}
```

* отклонение запроса - статус 401 - запрос от неаутенфицированного пользователя

```
{
  "detail": "Учетные данные не были предоставлены."
}
```

***
**Полный перечень запросов к API перечислен в документации ReDoc по адресу:**

```
"http://127.0.0.1:8000/redoc/"
```
***
