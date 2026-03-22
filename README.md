# Edu Core API: движок для образовательных систем

![Python](https://img.shields.io/badge/python-3.10+-blue.svg)
![Django](https://img.shields.io/badge/django-5.2-green.svg)
![DRF](https://img.shields.io/badge/DRF-3.16-red.svg)

**Edu Core API** — бэкенд на Django REST Framework для структуры курсов, материалов и тестирования. В проекте — кастомная модель пользователя, иерархия разделов и материалов, модуль тестов с вопросами и фиксацией результатов.

## Основной функционал

* **Разделы и материалы (`materials/`):** модели `Section` и `Material`, ViewSets для CRUD; материал привязан к разделу.
* **Пользователи (`users/`):** регистрация, вход по email, JWT (access / refresh).
* **Тестирование (`tests/`):** тесты, вопросы (один / несколько / текстовый ответ), варианты ответов, сдача теста и просмотр результатов.
* **Документация API:** Swagger UI (drf-yasg) по адресу `/swagger/`.
* **Права доступа:** в корне репозитория `permissions.py` — проверки по группам Django и владельцу объекта; у пользователя есть поле `role` (admin / teacher / student).

## Технологический стек

* **Framework:** Django, Django REST Framework.
* **База данных:** PostgreSQL (`django.db.backends.postgresql_psycopg2`).
* **Аутентификация:** JWT ([djangorestframework-simplejwt](https://django-rest-framework-simplejwt.readthedocs.io/)).
* **Документация:** drf-yasg (Swagger UI).
* **Прочее:** python-dotenv, django-cors-headers, Pillow (поле аватара).

## Структура приложений

| Путь | Назначение |
|------|------------|
| `config/` | Настройки Django, корневые URL |
| `materials/` | Разделы и материалы |
| `users/` | Пользователи, регистрация, выдача JWT |
| `tests/` | Тесты, вопросы, ответы, результаты |
| `permissions.py` | Классы разрешений DRF |

Префиксы маршрутов API: `users/`, `materials/`, `tests/`; админка: `admin/`.

## Установка и запуск

1. Клонируйте репозиторий:

   ```bash
   git clone https://github.com/AJLbN0H/edu-core-api.git
   cd edu-core-api
   ```

2. Убедитесь, что установлены **Python 3.10+** и **Poetry**, поднят **PostgreSQL**.

3. Скопируйте переменные окружения и заполните их (шаблон — `.env.sample`):

   * `SECRET_KEY`, `DEBUG` (`True` / `False`);
   * `NAME`, `USER`, `PASSWORD`, `HOST`, `PORT` — параметры БД.

4. Установите зависимости и примените миграции:

   ```bash
   poetry install
   poetry run python manage.py migrate
   ```

5. Запустите сервер разработки:

   ```bash
   poetry run python manage.py runserver
   ```

6. Откройте Swagger: [http://127.0.0.1:8000/swagger/](http://127.0.0.1:8000/swagger/).

### Полезные команды

```bash
poetry run python manage.py test
```

## Замечания по развёртыванию

* В `config/settings.py` заданы `CORS_ALLOWED_ORIGINS` и `CSRF_TRUSTED_ORIGINS` для `http://localhost:8000`; для другого фронтенда их нужно расширить.
* `ALLOWED_HOSTS` по умолчанию пустой — для продакшена задайте список хостов.

## Идеи для развития

* Контейнеризация (Docker / docker-compose).
* Единая модель прав на базе поля `role` и согласование с группами Django.
* Отдельная схема ReDoc или экспорт OpenAPI, если нужен второй вид документации.
