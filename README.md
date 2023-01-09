# API_Yatube

## Описание:

REST API для социальной сети Yatube

Аутентификация по JWT-токену

Поддерживает методы GET, POST, PUT, PATCH, DELETE

Предоставляет данные в формате JSON

## Стек технологий:
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

![DjangoREST](https://img.shields.io/badge/DJANGO-REST-ff1709?style=for-the-badge&logo=django&logoColor=white&color=ff1709&labelColor=gray)

![JWT](https://img.shields.io/badge/JWT-black?style=for-the-badge&logo=JSON%20web%20tokens)

![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)

## Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:
`git clone https://github.com/SidVi990/api_final_yatube.git`

Cоздать и активировать виртуальное окружение:
```
python3 -m venv env

source env/bin/activate
```
Установить зависимости из файла requirements.txt:
```
python3 -m pip install --upgrade pip

pip install -r requirements.txt
```
Выполнить миграции:
```
python3 manage.py migrate
```
Запустить проект:
```
python3 manage.py runserver`
```
## Документация к проекту

Документация для API после установки доступна по адресу `http://127.0.0.1:8000/redoc`

## Аутентификация

Выполните POST-запрос к `http://127.0.0.1:8000/api/v1/jwt/create/` передав поля username и password.

API вернет JWT-токен в формате:
```
{
    "refresh": "ХХХХХХХХХХХ",
    "access": "ХХХХХХХХХХХХ"
}
```
Токен вернётся в поле access, а данные из поля refresh нужны для обновления токена

При отправке запроcов передавайте токен в заголовке `Authorization: Bearer <токен>`

## Как работает API_Yatube

Пример http-запроса (POST) для создания поста:
```
url = 'http://127.0.0.1:8000/api/v1/posts/'
data = {'text': 'Your post'}
headers = {'Authorization': 'Bearer your_token'}
request = requests.post(url, data=data, headers=headers)
```
Ответ API_Yatube:
```
Статус- код 200

{
  "id": 0,
  "text": "string",
  "author": "string",
  "pub_date": "2020-08-20T14:15:22Z"
}
```
Пример http-запроса (GET) для получения списка подписчиков:
```
url = 'http://127.0.0.1:8000/api/v1/follow/'
headers = {'Authorization': 'Bearer your_token'}
request = requests.get(api, headers=headers)
```
Ответ API_Yatube:
```
Статус- код 200

[
  {
    "user": "string",
    "following": "string"
  }
]
```