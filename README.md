# Edu Core API: Engine для образовательных систем

![Python](https://img.shields.io/badge/python-3.11+-blue.svg)
![Django](https://img.shields.io/badge/django-5.2+-green.svg)
![DRF](https://img.shields.io/badge/DRF-latest-red.svg)

**Edu Core API** — это специализированное бэкенд-решение, сфокусированное на архитектуре контента образовательных платформ. Проект демонстрирует навыки проектирования гибких моделей данных и эффективного использования инструментов Django Rest Framework.

## Ключевой функционал
* **Управление разделами (Sections):** Иерархическая структура образовательных курсов.
* **Материалы и контент:** API для управления уроками, заданиями и дополнительными материалами.
* **Интеграция Swagger:** Полная спецификация эндпоинтов для удобного взаимодействия с фронтенд-командой.
* **Кастомные ViewSets:** Оптимизация кода за счет использования стандартных и кастомных наборов представлений DRF.

## Технологический стек
* **Framework:** Django Rest Framework.
* **Database:** PostgreSQL.
* **Auth:** Token-based authentication (DRF).
* **Documentation:** Swagger/ReDoc (drf-yasg).
* **Tools:** Python-dotenv, CORS-headers.

## Архитектура
Проект построен по модульному принципу:
* `materials/`: Ядро системы — разделы (Sections) и элементы (Items).
* `users/`: Логика регистрации и авторизации.

## Установка и запуск

1. Клонируйте репозиторий:

    git clone https://github.com/AJLbN0H/edu-core-api.git

2. Настройте файл .env:
Укажите параметры подключения к вашей БД.

3. Установите зависимости и примените миграции:

    poetry install
    python manage.py migrate

4. Запустите сервер:

    python manage.py runserver

## Roadmap
* Добавление системы тестирования знаний (Quizzes).
* Внедрение ролевой модели доступа (RBAC).
* Контейнеризация проекта через Docker.
