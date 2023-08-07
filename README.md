# YLab_project_1
Task from the YLab company. FastAPI + SQLalchemy + PostgreSQL + Pytest + Docker + Redis.

Для хранения переменных во время запуска Pytest использовал встроенное кэширование.
Тест подсчета подменю и блюд реализован в файле "application/tests/count_submenus_and_dishes_test.py". Он запускается вместе со всеми тестами.

Для хранения кеша API используется redis.

Проверка кода через линтеры в файле ".pre-commit-config.yaml". В корне проекта запустить команды "pre-commit install", затем "pre-commit run --all-files".

Для запуска из докера:

  1. Клонировать проект.
  2. Убрать расширение txt у файла ".env.txt".
  3. Если необходимо изменить параметры для базы данных.

    Запуск проекта и базы данных:

    1. Запустить команду "docker compose -f docker-compose.yaml up --build" из корня проекта.
    2. По адресу "0.0.0.0:8000" будет доступно API.
    3. Протестировать можно через Postman или вручную. Готовые тесты лежат в папке "Postman". Их необходимо импортировать в приложение Postman, далее выбрать "menu app" в качестве             environments. Для ручного тестирования использовать пути из файла "main.py".
    4. Тесты из папки "Тестовый сценарий" проходить только с пустой базай данных.
    5. Тесты из папки "api" проходить только с наполненной базой данных.


    Запуск тестов pytest и базы данных:

    1. Остановить контейнеры проекта и базы данных, если запущены. Если контйнеры остановлены перейти к шагу №2.
    2. Запустить команду "docker compose -f docker-compose-test.yaml up --build" из корня проекта.


Для локального запуска:

  1. Клонировать проект.
  2. Установить библиотеки из файла "requirements.txt".
  3. Убрать расширение txt у файла ".env.txt". Изменить параметры для базы данных, если необходимо.  
  4. Запустить на локальной машине PostgreSQL.
  5. В файле ".env" указать данные для базы данных. В значении "POSTGRES_SERVER" указать "localhost" или "127.0.0.1".

    Запуск проекта:

    1. Запустить команду "uvicorn application.main:app --reload" из корня проекта.
    2. Использовать шаги с 3-го по 5-й из инструкции "Для запуска из докера/ Запуск проекта и базы данных".


    Запуск тестов pytest:

    1. Желательно, чтобы база была пустая.
    2. Из корня проекта запустить команду "pytest -v" для отображения данных о прохождении тестов. Для отображения данных ответа каждого теста запустить "pytest -s".
