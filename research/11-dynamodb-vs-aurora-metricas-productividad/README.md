---
id: 11-dynamodb-vs-aurora-metricas-productividad
title: "¿Cuándo usarías DynamoDB frente a Aurora (MySQL/PostgreSQL) para medir productividad de ingeniería?"
block: "Bloque 3: AWS, Bases de Datos & Arquitectura Cloud"
block_number: 3
question_number: 11
tags:
  - aws
  - dynamodb
  - aurora
  - postgresql
  - single-table-design
  - database
aliases:
  - dynamodb-vs-aurora
status: documented
created_at: 2026-10-19
has_code_benchmark: false
---

### 11. "¿Cuándo usarías DynamoDB frente a Aurora (MySQL/PostgreSQL) para medir productividad de ingeniería?"

- **Respuesta:**
- **DynamoDB (NoSQL / Key-Value):** Ideal para almacenar eventos crudos de alta frecuencia y baja latencia (ej. webhooks de GitHub, eventos de CI/CD, métricas de telemetría de sensores/desarrolladores). Se diseña con _Single-Table Design_ sabiendo los patrones de acceso de antemano (ej. `PK: REPO#123`, `SK: EVENT#TIMESTAMP`).
- **Aurora (Relacional):** Necesario para el modelo de datos analítico y relacional: entidades con relaciones complejas (Equipos $\rightarrow$ Desarrolladores $\rightarrow$ Repositorios $\rightarrow$ Proyectos de Jira) y consultas ad-hoc con `JOIN`s, agregaciones de percentiles y dashboards de productividad.
