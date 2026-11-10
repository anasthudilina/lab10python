# Bank Account Service API

REST API для системи банківських рахунків (Лабораторна робота №10). 
Проєкт підготовлений до production-використання: містить пакетну збірку, Docker-контейнеризацію, конфігурацію через змінні оточення та CI/CD pipeline.

## Features
- Управління клієнтами та рахунками (CRUD).
- Поповнення, списання та атомарні перекази коштів.
- Історія транзакцій.
- Захист від від'ємного балансу.
- Конфігурація через `.env` (Pydantic Settings).
- Контейнеризація (Docker).
- Автоматичне тестування, лінтінг та перевірка типів (GitHub Actions).

## Requirements
- Python 3.11+
- Docker (для запуску в контейнері)

## Installation
Для локальної розробки встановіть пакет з усіма залежностями:
```bash
python -m venv .venv
source .venv/bin/activate  # На Windows: .venv\Scripts\activate
pip install -e ".[dev]"
Configuration
Створіть файл .env у корені проєкту (на основі .env.example):

env
APP_NAME="Bank Account Service"
ENVIRONMENT="development"
DATABASE_URL="sqlite:///bank.db"
LOG_LEVEL="INFO"
Running locally
Запуск сервера розробки:

bash
uvicorn bank_account_service.api:app --reload
Running with Docker
Збірка образу:

bash
docker build -t bank-account-service:1.0 .
Запуск контейнера:

bash
docker run --rm -p 8000:8000 --env-file .env bank-account-service:1.0
API Documentation
Після запуску сервера документація доступна за адресами:

Swagger UI: http://localhost:8000/docs

ReDoc: http://localhost:8000/redoc

Health check: http://localhost:8000/health

Testing
Запуск тестів:

bash
pytest -v
Перевірка стилю та типів:

bash
ruff check .
mypy src
Project structure
text
lab10/
├── .github/workflows/ci.yml  # CI/CD pipeline
├── src/bank_account_service # Основний код
├── tests/                    # Тести
├── Dockerfile                # Інструкція для збірки образу
├── pyproject.toml            # Метадані та залежності
└── README.md
CI/CD
Проєкт налаштований на автоматичну перевірку через GitHub Actions. При кожному пуші в гілку main виконуються:

Перевірка стилю (ruff).

Перевірка типів (mypy).

Запуск тестів (pytest).

Збірка Python-пакета.

Збірка Docker-образу.


