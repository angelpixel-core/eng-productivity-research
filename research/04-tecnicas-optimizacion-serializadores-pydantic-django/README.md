---
id: 04-tecnicas-optimizacion-serializadores-pydantic-django
title: "¿Qué técnicas usas para evitar que los serializadores de datos (Pydantic/Django Serializers) sean el cuello de botella?"
block: "Bloque 1: Python Profiling, Optimización & Performance"
block_number: 1
question_number: 4
tags:
  - pydantic
  - pydantic-core
  - orjson
  - serialization
  - performance
aliases:
  - optimizacion-serializadores-pydantic
status: documented
created_at: 2026-10-19
has_code_benchmark: false
---

### 4. "¿Qué técnicas usas para evitar que los serializadores de datos (Pydantic/Django Serializers) sean el cuello de botella?"

- **Respuesta:**
- En **FastAPI con Pydantic v2:** Aprovechar que el motor de validación (`pydantic-core`) corre en Rust. Evitar validadores `@validator` o `@field_validator` lentos con lógica de Python puro en colecciones de miles de elementos.
- Usar serialización selectiva (`model_dump(include={...})`) para no transformar campos innecesarios.
- Si se procesan volúmenes gigantescos de logs de CI/CD hacia respuestas JSON, saltar la re-validación de salida utilizando `orjson` como reemplazo directo del módulo `json` estándar, reduciendo el tiempo de serialización hasta 6 veces.
