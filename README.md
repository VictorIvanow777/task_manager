# Task Manager — Контейнеризация с Docker Compose

## Описание

Този проект представлява уеб базирано приложение за управление на задачи, което е контейнеризирано с помощта на Docker и Docker Compose. Проектът се състои от три отделни компонента:

- MySQL база данни
- Node.js REST API, който комуникира с базата
- Уеб клиент (HTML + JS), който визуализира задачите чрез API

---


---

## Как работи всеки компонент

###  1. `db` – MySQL база данни
- Използва Docker образ `mysql:8.0`
- Автоматично създава база данни `taskdb`
- Създава таблица `tasks` и добавя примерни записи
- Данните се зареждат чрез `init.sql`

### 2. `api` – Node.js бекенд
- Създаден с Express и mysql2
- REST API с един маршрут: `GET /tasks`
- Чете задачи от базата данни и връща JSON отговор
- Достъпен на порт `3000`

### 3. `web` – HTML + JavaScript
- Статичен уеб интерфейс, обслужван от Nginx
- Прави `fetch` заявка към API-то, за да покаже задачите
- Стартира се на порт `8080`

---

## Стартиране на проекта

1. Уверете се, че имате инсталиран [Docker](https://www.docker.com/products/docker-desktop)
2. Клонирайте хранилището:
```bash
git clone https://github.com/your-username/task-manager.git
cd task-manager

## Изпълнете:
docker-compose up --build
---
Отворете браузър на адрес:
==>http://localhost:8080 – уеб интерфейс
==>http://localhost:3000/tasks – API в JSON формат



