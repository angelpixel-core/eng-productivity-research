---
id: 03-como-evitas-bloquear-event-loop-fastapi
title: "¿Cómo evitas bloquear el Event Loop en FastAPI al ejecutar tareas pesadas de parsing de código o cálculo de métricas?"
block: "Bloque 1: Python Profiling, Optimización & Performance"
block_number: 1
question_number: 3
tags:
  - fastapi
  - asyncio
  - event-loop
  - sqs
  - threadpool
  - performance
aliases:
  - evitar-bloqueo-event-loop-fastapi
status: documented
created_at: 2026-10-19
has_code_benchmark: false
---

### 3. "¿Cómo evitas bloquear el Event Loop en FastAPI al ejecutar tareas pesadas de parsing de código o cálculo de métricas?"

- **Respuesta:**
  Si un endpoint asíncrono ejecuta una tarea ligada a CPU (CPU-bound) como parsear diffs gigantes de Git:
- Ejecutarlo directamente dentro del `async def` congela el Event Loop para todos los demás requests concurrentes.
- **Solución intermedia:** Delegarlo al threadpool de AnyIO mediante `fastapi.concurrency.run_in_threadpool()` o `asyncio.to_thread()`, liberando el loop.
- **Solución de arquitectura para producción:** Desacoplar la petición síncrona. La API valida el evento, responde `202 Accepted` y encola la tarea en **AWS SQS** para que un worker dedicado (o un proceso en `ProcessPoolExecutor`) lo procese sin penalizar el tráfico web.
