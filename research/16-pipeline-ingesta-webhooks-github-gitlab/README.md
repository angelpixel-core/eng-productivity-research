---
id: 16-pipeline-ingesta-webhooks-github-gitlab
title: "¿Cómo arquitectarías un pipeline para ingerir y procesar webhooks de GitHub/GitLab para miles de desarrolladores sin perder eventos?"
block: "Bloque 4: Big Data Pipelines & Liderazgo Senior"
block_number: 4
question_number: 16
tags:
  - webhooks
  - github-api
  - sqs
  - lambda
  - dlq
  - event-driven
  - resilience
aliases:
  - pipeline-ingesta-webhooks
status: documented
created_at: 2026-10-19
has_code_benchmark: false
---

### 16. "¿Cómo arquitectarías un pipeline para ingerir y procesar webhooks de GitHub/GitLab para miles de desarrolladores sin perder eventos?"

- **Respuesta:**

1. **Ingesta ligera:** Un endpoint simple en API Gateway + Lambda (o FastAPI) valida la firma criptográfica del webhook (HMAC SHA-256), responde `200 OK` en <100 ms para evitar que GitHub reintente por timeout, y deposita el payload crudo en **Amazon SQS**.
2. **Buffer y Desacople:** SQS absorbe los picos de commits durante las horas pico de oficina.
3. **Procesamiento escalable:** Workers en ECS o funciones Lambda consumen mensajes en batches, deduplican por ID de entrega (`X-GitHub-Delivery`) y procesan las métricas.
4. **Tolerancia a fallos:** Se configura una **Dead-Letter Queue (DLQ)** para capturar mensajes malformados tras 3 reintentos fallidos, alertando a CloudWatch sin detener el pipeline.
