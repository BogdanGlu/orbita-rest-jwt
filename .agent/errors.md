# Ошибки и исправления (реальные случаи)
| Ошибка | Причина | Исправление |
|---|---|---|
| Docker: Virtual Machine Platform not enabled | компонент Windows выключен, нет прав админа | wsl --install от администратора + перезагрузка |
| 500 при Authorize; relation "user" does not exist | миграции не применены в dev-режиме | alembic upgrade head + python app/initial_data.py |
| npm не распознано | Node.js не установлен | установка Node.js LTS |
| npm.ps1: выполнение сценариев отключено | политика PowerShell Restricted | Set-ExecutionPolicy -Scope CurrentUser RemoteSigned |
| WSL is unresponsive | сбой WSL после сна/нагрузки | перезагрузка ПК, docker compose up -d |
| на 5173 посторонняя страница | frontend не входит в compose этой версии | npm run dev + собственный клиент /app.html |
| код «горит красным» в VS Code | несохранённый файл в режиме CSS | Save As app.html в frontend/public, язык HTML |
