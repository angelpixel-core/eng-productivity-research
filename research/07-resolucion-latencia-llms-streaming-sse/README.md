---
id: 07-resolucion-latencia-llms-streaming-sse
title: "¿Cómo resolverías la latencia inherente de los LLMs para que la herramienta interna sea reactiva?"
block: "Bloque 2: Integración de IA/LLMs y Flujos Productivos"
block_number: 2
question_number: 7
tags:
  - llm
  - sse
  - streaming
  - sqs
  - latency
  - fastapi
aliases:
  - latencia-llms-streaming-sse
status: documented
created_at: 2026-10-19
has_code_benchmark: false
---

### 7. "¿Cómo resolverías la latencia inherente de los LLMs para que la herramienta interna sea reactiva?"

- **Respuesta:**
- Para interfaces interactivas (ej. copiloto de revisiones en tiempo real): **Streaming end-to-end**. El backend de FastAPI consume los tokens del SDK en modo streaming y los canaliza al cliente web usando **Server-Sent Events (SSE)**. El usuario percibe la respuesta en <500 ms (Time To First Token).
- Para análisis por lotes (ej. auditar todos los PRs de la semana): Ingesta encolada en **SQS**, consumo mediante workers que aplican límites de concurrencia y backoff exponencial para respetar los rate-limits (TPM/RPM) del proveedor de IA.
