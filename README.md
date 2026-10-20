# Engineering Productivity Platform & Technical Knowledge Base

Esta descripción tiene un foco **marcadamente distinto** a la de un marketplace convencional:

1. **El Producto:** Herramienta interna de IA para medir y mejorar la **productividad de ingeniería** (métricas de PRs, ciclos de delivery tipo DORA, commits, tickets de Jira/Linear, revisiones de código asistidas por LLMs).
2. **El Cloud y Persistencia:** El foco principal se centra en **AWS** (`Lambda`, `DynamoDB`, `Aurora MySQL/PostgreSQL`, `ElastiCache/Redis`).
3. **Big Data + Pipelines:** Ya no es solo una API síncrona; requiere procesar flujos de telemetría y eventos de desarrollo a escala.
4. **Performance & Profiling explícito:** La descripción exige literalmente _"troubleshoot, profile, and optimize backend systems and AI integrations"_.

A continuación tienes el banco de **20 preguntas técnicas y situacionales** estructurado en 4 bloques temáticos clave, con respuestas directas, métricas, patrones Senior/Staff y código ejecutable de referencia en carpetas modulares bajo [`research/`](./research/).

---

## Índice Temático de Investigación y Benchmarks

### Bloque 1: Python Profiling, Optimización & Performance (5 Preguntas)

- [01. Profiling y optimización de un servicio Python con consumo excesivo de CPU/RAM](./research/01-como-encarar-profiling-y-optimizacion/README.md) *(Incluye benchmark ejecutable en Python)*
- [02. Cuándo usar Django vs. FastAPI en una herramienta de productividad de ingeniería](./research/02-cuando-usarias-django-vs-fastapi/README.md)
- [03. Cómo evitar bloquear el Event Loop en FastAPI en tareas CPU-bound](./research/03-como-evitas-bloquear-event-loop-fastapi/README.md)
- [04. Técnicas para evitar cuellos de botella en serializadores (Pydantic v2 / Django)](./research/04-tecnicas-optimizacion-serializadores-pydantic-django/README.md)
- [05. Manejo del Global Interpreter Lock (GIL) en pipelines de Big Data en Python](./research/05-manejo-gil-pipelines-big-data-python/README.md)

---

### Bloque 2: Integración de IA/LLMs y Flujos Productivos (5 Preguntas)

- [06. Integración de LLMs para análisis de PRs/tickets controlando costos y timeouts](./research/06-integracion-llms-analisis-prs-tickets/README.md)
- [07. Estrategias frente a la latencia inherente de LLMs (Streaming SSE / SQS)](./research/07-resolucion-latencia-llms-streaming-sse/README.md)
- [08. Evaluación de consistencia y mitigación de alucinaciones en métricas de código](./research/08-evaluacion-consistencia-evitar-alucinaciones-metricas-ia/README.md)
- [09. Control de contexto y ventana de tokens con Map-Reduce / Refine jerárquico](./research/09-control-contexto-ventana-tokens-map-reduce/README.md)
- [10. Trazabilidad y observabilidad de llamadas a LLMs en producción (OpenTelemetry / FinOps)](./research/10-trazabilidad-observabilidad-llamadas-llms/README.md)

---

### Bloque 3: AWS, Bases de Datos & Arquitectura Cloud (5 Preguntas)

- [11. Criterios de elección entre DynamoDB vs. Aurora para productividad de ingeniería](./research/11-dynamodb-vs-aurora-metricas-productividad/README.md)
- [12. Integración de ElastiCache (Redis) para optimización de dashboards y métricas](./research/12-elasticache-redis-optimizacion-dashboards/README.md)
- [13. Criterios arquitectónicos: AWS Lambda vs. servicios contenedorizados (ECS/Fargate)](./research/13-aws-lambda-vs-ecs-fargate-criterios-arquitectura/README.md)
- [14. Diseño de tablas en DynamoDB para mitigar particiones calientes (Write Sharding)](./research/14-diseno-dynamodb-hot-partitions-write-sharding/README.md)
- [15. Estrategias de migración de esquema sin downtime ni bloqueos en Aurora](./research/15-migraciones-esquema-aurora-sin-downtime/README.md)

---

### Bloque 4: Big Data Pipelines & Liderazgo Senior (5 Preguntas)

- [16. Arquitectura de pipeline para ingesta masiva de webhooks de Git sin pérdida de eventos](./research/16-pipeline-ingesta-webhooks-github-gitlab/README.md)
- [17. Procesamiento de gigabytes de telemetría de CI/CD con Polars, DuckDB y Parquet](./research/17-pipelines-big-data-telemetria-cicd-polars-duckdb-spark/README.md)
- [18. Cálculo de métricas DORA con precisión histórica mediante Event Sourcing](./research/18-calculo-metricas-dora-event-sourcing/README.md)
- [19. Liderazgo técnico: mentoría, automatización en CI/CD y ADRs en el equipo](./research/19-liderazgo-mentorias-calidad-estandares-senior/README.md)
- [20. Plan de acción de dos semanas para estabilizar y optimizar prototipos lentos](./research/20-plan-de-accion-primeras-dos-semanas-estabilizacion/README.md)

---

## Cómo conectar tus proyectos personales con esta Job Description

- **Tu AI Conversation Platform:** Es tu prueba irrefutable de que sabes integrar LLMs con FastAPI, streaming (SSE), Pydantic v2 y arquitectura limpia orientada a contratos.
- **Tu experiencia en Nubi / Bitex / Google:** Respalda tu dominio de AWS, transacciones financieras, resiliencia ante fallos y pipelines distribuidos con colas/eventos.
- **Tu proyecto de Streamlit / Dashboards:** Demuestra que sabes construir interfaces analíticas y reportes de métricas para stakeholders internos de forma ágil.
