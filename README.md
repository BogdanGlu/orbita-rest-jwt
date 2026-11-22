# ОРБИТА — клиент-серверное приложение с REST API и JWT-авторизацией

Учебный проект. База: https://github.com/fastapi/full-stack-fastapi-template
(адаптирован: собственный клиент «ОРБИТА», артефакты работы с ИИ-агентом, документация).

## Стек
- Backend: Python, FastAPI, SQLModel, PostgreSQL, Alembic
- Frontend: React + TypeScript (Vite) и собственный клиент «ОРБИТА» (frontend/public/app.html)
- Авторизация: JWT (OAuth2 Password Flow), роли user/superuser
- Инфраструктура: Docker Compose (db, backend, adminer, mailpit, proxy)

## Запуск
1. Docker Desktop + Git + Node.js LTS
2. docker compose up -d --build
3. Миграции (dev-режим не применяет их сам):
   docker compose exec backend alembic upgrade head
   docker compose exec backend python app/initial_data.py
4. Клиент: cd frontend && npm install && npm run dev
5. Адреса:
   - http://localhost:5173 — шаблонный React-клиент
   - http://localhost:5173/app.html — собственный клиент «ОРБИТА»
   - http://localhost:8000/docs — Swagger (REST API)
   - http://localhost:8080 — Adminer, http://localhost:8025 — Mailpit
6. Вход: FIRST_SUPERUSER / FIRST_SUPERUSER_PASSWORD из .env (демо: admin@example.com / changethis)

## Тесты
docker compose exec backend python -m pytest

## Основные эндпоинты
| Метод | Путь | Доступ | Описание |
|---|---|---|---|
| POST | /api/v1/login/access-token | все | вход, выдача JWT |
| POST | /api/v1/users/signup | все | регистрация |
| GET | /api/v1/users/me | Bearer | профиль |
| GET/POST | /api/v1/users/ | superuser | пользователи |
| GET/POST/PUT/DELETE | /api/v1/items/ | Bearer | CRUD записей владельца |
| GET | /api/v1/utils/health-check/ | все | здоровье сервера |

## Документация и артефакты
- docs/architecture.md — схема и соответствие структуре задания
- docs/screenshots/ — скриншоты, docs/demo.mp4 — демо (30–60 сек)
- PROMPTS.md / REFLECTION.md / .agent/ — дневник промптов, рефлексия, ошибки
