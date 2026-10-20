---
id: 05-manejo-gil-pipelines-big-data-python
title: "¿Cómo manejas el Global Interpreter Lock (GIL) en pipelines de Big Data en Python?"
block: "Bloque 1: Python Profiling, Optimización & Performance"
block_number: 1
question_number: 5
tags:
  - gil
  - multiprocessing
  - asyncio
  - polars
  - spark
  - concurrency
aliases:
  - manejo-gil-python
status: documented
created_at: 2026-10-19
has_code_benchmark: false
---

### 5. "¿Cómo manejas el Global Interpreter Lock (GIL) en pipelines de Big Data en Python?"

- **Respuesta:**
  El GIL impide que múltiples hilos de Python ejecuten bytecode simultáneamente en múltiples cores.
- Para **I/O-bound** (llamadas a GitHub API, consultas SQL, APIs de LLMs): Uso `asyncio` o `ThreadPoolExecutor`; el hilo libera el GIL mientras espera la respuesta de red.
- Para **CPU-bound** (análisis sintáctico de código, agregaciones estadísticas masivas): Se debe usar **multiprocessing** (`ProcessPoolExecutor`) para instanciar procesos independientes de Python con sus propias memorias y GILs, o delegar el cómputo a frameworks distribuidos/vectorizados (Spark/Polars) que operan fuera del runtime de CPython.
