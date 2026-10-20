---
id: 02-cuando-usarias-django-vs-fastapi
title: "¿Cuándo usarías Django vs. FastAPI en una herramienta de productividad de ingeniería?"
block: "Bloque 1: Python Profiling, Optimización & Performance"
block_number: 1
question_number: 2
tags:
  - python
  - fastapi
  - django
  - architecture
  - engineering-productivity
aliases:
  - django-vs-fastapi
status: documented
created_at: 2026-10-19
has_code_benchmark: false
---

### 2. "¿Cuándo usarías Django vs. FastAPI en una herramienta de productividad de ingeniería?"

- **Respuesta:**
- **FastAPI:** Lo elijo para microservicios de ingesta de alta concurrencia, pipelines de streaming de inferencia LLM (vía SSE) o APIs REST asíncronas de bajo footprint que se comunican con workers externos.
- **Django:** Lo elijo si la herramienta requiere un backoffice administrativo nativo (Django Admin), autenticación empresarial compleja basada en sesiones, y si el flujo principal depende fuertemente del ORM para consultas transaccionales estructuradas sin necesidad de asincronía masiva en el Event Loop.
- **Estrategia híbrida:** Usar FastAPI para la capa de ingesta/inferencia y workers en background (Celery) sobre los mismos modelos.
