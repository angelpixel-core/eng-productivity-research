---
id: 13-aws-lambda-vs-ecs-fargate-criterios-arquitectura
title: "¿Cuándo conviene usar AWS Lambda y cuándo un servicio contenedorizado (ECS/Fargate) para este backend?"
block: "Bloque 3: AWS, Bases de Datos & Arquitectura Cloud"
block_number: 3
question_number: 13
tags:
  - aws
  - lambda
  - ecs
  - fargate
  - serverless
  - containers
  - architecture
aliases:
  - lambda-vs-fargate
status: documented
created_at: 2026-10-19
has_code_benchmark: false
---

### 13. "¿Cuándo conviene usar AWS Lambda y cuándo un servicio contenedorizado (ECS/Fargate) para este backend?"

- **Respuesta:**
- **AWS Lambda:** Ideal para procesamiento asíncrono y reactivo guiado por eventos: consumidores de colas SQS, webhooks de GitHub que se ejecutan en ráfagas cortas, o tareas cron de extracción de datos.
- **ECS / Fargate (o EKS):** Indispensable para la API web principal que requiere latencias estables sin _cold starts_, APIs con WebSockets/SSE de larga duración, o tareas de análisis de código pesadas que superan los límites de ejecución de 15 minutos o memoria de Lambda.
