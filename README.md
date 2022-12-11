# api_final
api final
### Описание
Реализация API для проекта Yatube.<br>
Доступ к API у неаутентифицированных пользователей только для чтения.<br>
Исключение эндпоинд /follow/: доступ предоставляться только аутентифицированным<br> пользователям. Для аутентификации используйте JWT-токены. Эндпоинт /posts/ - работает<br>
с пагинацией. Вы можете самостоятельно определять, какое число объектов вернётся<br>
(параметр limit) и с какого по счёту объекта начать отсчёт (параметр offset).<br>
Эндпоинт /follow/ - возможен поиск по подпискам по параметру search.<br>
### Примеры возможных запросов
- Получение публикации по id<br>
```
GET http://127.0.0.1:8000/api/v1/posts/{id}/
``` 
<details><summary>Response 200</summary> 
{<br>
  "id": 0,<br>
  "author": "string",<br>
  "text": "string",<br>
  "pub_date": "2019-08-24T14:15:22Z",<br>
  "image": "string",<br>
  "group": 0<br>
}
</details>
<details><summary>Response 404</summary> 
{<br>
  "detail": "Страница не найдена."<br>
}
</details>

- Получение информации о сообществе по id
```
GET http://127.0.0.1:8000/api/v1/groups/{id}/
```
<details><summary>Response 200</summary>
{<br>
  "id": 0,<br>
  "title": "string",<br>
  "slug": "string",<br>
  "description": "string"<br>
}
</details>
<details><summary>Response 404</summary>
{<br>
  "detail": "Страница не найдена."<br>
}
</details>

- Возвращает все подписки пользователя, сделавшего запрос
```
GET http://127.0.0.1:8000/api/v1/follow/<br>
```
<details><summary>Response 200</summary>
{<br>
  "user": "string",<br>
  "following": "string"<br>
}
</details>
<details><summary>Response 401</summary>
{<br>
  "detail": "Учетные данные не были предоставлены."<br>
}
</details>

### Технологии
![image](https://img.shields.io/badge/Python-FFD43B?style=for-the-badge&logo=python&logoColor=blue) Python 3.9<br/>
![image](https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=green) Django 3.2
### Запуск проекта в dev-режиме
- Клонируйте репозиторий
```
git clone git@github.com:AtabekovaEkaterina/api_final_yatube.git
```

- Перейдите в директорию проекта, далее установите и активируйте виртуальное окружение
```
python3 -m venv env
```
```
source env/bin/activate
```
- Установите зависимости из файла requirements.txt
```
pip install -r requirements.txt
```
- Выполните миграции:
```
python3 manage.py migrate
```
- Запустите проект:
```
python3 manage.py runserver
```
### Автор
Екатерина