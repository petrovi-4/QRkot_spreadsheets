# Проект поддержки котиков
## Описание
Проект написан на фреймворке FastAPI Python с возможностью формировать отчеты о закрытых проектах по сбору средств в Google Sheets с использование хранилища Google Drive.  
Это API сервиса по сбору средств для финансирования благотворительных проектов. В сервисе реализована возможность регистрации пользователей, добавления благотворительных проектов и пожертвований, которые распределяются по открытым проектам.    

Настроено автоматическое создание суперпользователя при запуске проекта.

## Технологии
* [**Python**](https://www.python.org/)
* [**FastAPI**](https://fastapi.tiangolo.com/)
* [**SQLAlchemy**](https://pypi.org/project/SQLAlchemy/)
* [**Alembic**](https://pypi.org/project/alembic/)
* [**Pydantic**](https://pypi.org/project/pydantic/)
* [**Asyncio**](https://docs.python.org/3/library/asyncio.html)
* [**Google API**](https://console.cloud.google.com/apis)
* [**Google Sheets**](https://www.google.ru/intl/ru/sheets/about/)
* [**Google Drive**](https://www.google.com/drive/)


## Как запустить
**Клонировать репозиторий**

```
git clone https://github.com/petrovi-4/cat_charity_fund.git
```
**Создать и активировать виртуальное окружение**

```
python3 -m venv venv
source venv/bin/activate
```
**Установить зависимости из файла requirements.txt**

```
python -m pip install --upgrade pip
pip install -r requirements.txt
```
**Создать файл .env и ввести переменные окружени**

```
# Переменные для работы приложения
APP_TITLE=<Ваше название>
APP_DESCRIPTION=<Ваше Описание>
DATABASE_URL=sqlite+aiosqlite:///./<название базы данных>.db
SECRET=<Ваше секретное слово>
FIRST_SUPERUSER_EMAIL=<email суперюзера>
FIRST_SUPERUSER_PASSWORD=<пароль суперюзера>

# Переменные для работы с Google API
TYPE=service_account
PROJECT_ID=<идентификатор>
PRIVATE_KEY_ID=<id приватного ключа>
PRIVATE_KEY="-----BEGIN PRIVATE KEY-----<приватный ключ>-----END PRIVATE KEY-----\n"
CLIENT_EMAIL=<email сервисного аккаунта>
CLIENT_ID=<id сервисного аккаунта>
AUTH_URI=https://accounts.google.com/o/oauth2/auth
TOKEN_URI=https://oauth2.googleapis.com/token
AUTH_PROVIDER_X509_CERT_URL=https://www.googleapis.com/oauth2/v1/certs
CLIENT_X509_CERT_URL=<ссылка>
EMAIL=<email пользователя>
```
**Запустить проект**

```
uvicorn app.main:app --reload
```
**Сервис будет запущен и доступен по следующим адресам:**

**http://127.0.0.1:8000** - API  
**http://127.0.0.1:8000/docs** - автоматически сгенерированная документация Swagger  
**http://127.0.0.1:8000/redoc** - автоматически сгенерированная документация ReDoc

**После запуска доступны следующие эндпоинты:**

**Регистрация и аутентификация:**  

* `/auth/register` - регистрация пользователя  
* `/auth/jwt/login` - аутентификация пользователя (получение jwt-токена)  
* `/auth/jwt/logout` - выход (сброс jwt-токена) 
 
**Пользователи:**  

* `/users/me` - получение и изменение данных аутентифицированного пользователя  
* `/users/{id}` - получение и изменение данных пользователя по id  

**Благотворительные проекты:**

* `/charity_project/` - получение списка проектов и создание нового  
* `/charity\_project/{project\_id}` - изменение и удаление существующего проекта  

**Пожертвования:** 

* `/donation/` - получение списка всех пожертвований и создание пожертвования  
* `/donation/my` - получение списка всех пожертвований аутентифицированного пользователя 

**Отчеты в Google Sheets**  

* `/google` - получение отчета о профинансированных (закрытых) проектах в формате Google Sheets. Отчет выгружается в Google Drive пользователя указанного в .env.

**Автор**  
[Мартынов Сергей](https://github.com/petrovi-4)

![GitHub User's stars](https://img.shields.io/github/stars/petrovi-4?label=Stars&style=social)
![licence](https://img.shields.io/badge/licence-GPL--3.0-green)