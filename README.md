[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/LP9Y-HT-)
# LKS URL Shortener App

Application monorepo for the LKS URL Shortener. Contains three services deployed as ECS Fargate containers behind a single ALB.

---

## Services

| Service               | Directory    | Port | Description                               |
| --------------------- | ------------ | ---- | ----------------------------------------- |
| **shortener-api**     | `api/`       | 3000 | URL creation, short-link redirect, delete |
| **analytics-service** | `analytics/` | 3001 | SQS consumer + click stats API            |
| **frontend**          | `frontend/`  | 80   | React SPA served by nginx                 |

See each service's `README.md` for setup and API details.

---

## Run with Docker Compose

From the **repository root**:

```bash
docker compose up --build
```

| Service                     | Local URL               |
| --------------------------- | ----------------------- |
| Frontend                    | <http://localhost:8080> |
| shortener-api               | <http://localhost:3000> |
| analytics-service           | <http://localhost:3001> |
| PostgreSQL                  | localhost:5432          |
| LocalStack (SQS + DynamoDB) | <http://localhost:4566> |

To stop and remove containers:

```bash
docker compose down
```
