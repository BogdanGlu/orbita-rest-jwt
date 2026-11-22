# Архитектура
Клиенты (React / «ОРБИТА») ──HTTP /api/v1──> FastAPI (backend/app)
  frontend/src/components → UI                api/routes → REST-эндпоинты
  frontend/public/app.html → свой клиент      crud.py → работа с БД (services)
                                              core/security.py → JWT, хеширование
                                              models.py → SQLModel, alembic → миграции
                                                     │
                                              PostgreSQL (db в Docker)
Авторизация: POST /login/access-token → JWT → Authorization: Bearer →
get_current_user / get_current_active_superuser защищают роуты; чужие записи недоступны.
«ОРБИТА»: журнал API, инспектор JWT, CRUD с оптимистичными обновлениями и отменой удаления.

## Соответствие структуре задания (структура примерная)
| В задании | В проекте |
|---|---|
| src/ | backend/app + frontend/src |
| main.* | backend/app/main.py |
| components/ | frontend/src/components |
| services/ | backend/app/crud.py, frontend/src/client |
| utils/ | backend/app/utils.py, backend/app/core |
| styles/ | frontend/src (темы), стили «ОРБИТА» в app.html |
| tests/ | backend/app/tests (+ playwright) |
| package.json/requirements | frontend/package.json, backend/pyproject.toml |
