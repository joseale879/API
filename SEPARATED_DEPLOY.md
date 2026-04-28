# Deploy Separado por Capa

Este proyecto corre en 3 repos/capas independientes:

- `proyecto-liquibase` [(PostgreSQL + Liquibase)](https://github.com/joseale879/proyecto-liquibase)
- `proyecto-backend` (Spring Boot API)https://github.com/joseale879/proyecto-backend
- `proyecto-frontend` (React/Vite)https://github.com/joseale879/proyecto-frontend

Todos se conectan por la red Docker: `api_app-network`.

## Repositorios Git

- `proyecto-liquibase`: `PEGAR_LINK_GIT_AQUI`
- `proyecto-backend`: `PEGAR_LINK_GIT_AQUI`
- `proyecto-frontend`: `PEGAR_LINK_GIT_AQUI`

## Conexiones y credenciales

- DB Host (desde Docker): `db`
- DB Host (desde tu PC): `localhost`
- DB Port: `5432`
- DB Name: `tareas_db`
- DB User: `postgres`
- DB Password: `postgres`

## Variables importantes

- Backend:
  - `SPRING_DATASOURCE_URL=jdbc:postgresql://db:5432/tareas_db`
  - `SPRING_DATASOURCE_USERNAME=postgres`
  - `SPRING_DATASOURCE_PASSWORD=postgres`
- Frontend:
  - `VITE_API_URL=http://localhost:8080`

## Orden de ejecución

```bash
docker compose -f proyecto-liquibase/docker-compose.db.yml up -d --build
docker compose -f proyecto-backend/docker-compose.backend.yml up -d --build
docker compose -f proyecto-frontend/docker-compose.frontend.yml up -d --build
```

## Verificación

- Frontend: `http://localhost:3000`
- Backend API: `http://localhost:8080/api/usuarios`
- Swagger: `http://localhost:8080/swagger-ui.html`
- PostgreSQL: `localhost:5432`

## Apagado

```bash
docker compose -f proyecto-frontend/docker-compose.frontend.yml down
docker compose -f proyecto-backend/docker-compose.backend.yml down
docker compose -f proyecto-liquibase/docker-compose.db.yml down
```
