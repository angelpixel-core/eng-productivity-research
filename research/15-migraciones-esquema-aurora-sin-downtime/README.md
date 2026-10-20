---
id: 15-migraciones-esquema-aurora-sin-downtime
title: "¿Cómo manejas migraciones de esquema en Aurora MySQL/Postgres en producción sin bloquear tablas críticas?"
block: "Bloque 3: AWS, Bases de Datos & Arquitectura Cloud"
block_number: 3
question_number: 15
tags:
  - aws
  - aurora
  - alembic
  - database-migrations
  - zero-downtime
  - sql
aliases:
  - migraciones-esquema-aurora-zero-downtime
status: documented
created_at: 2026-10-19
has_code_benchmark: false
---

### 15. "¿Cómo manejas migraciones de esquema en Aurora MySQL/Postgres en producción sin bloquear tablas críticas?"

- **Respuesta:**
- Con herramientas de migración (Alembic en SQLAlchemy o Django Migrations), evitar operaciones que bloqueen tablas enteras (_exclusive table locks_) en producción.
- **Regla de oro:** Aplicar migraciones compatibles hacia atrás y en fases:

1. Agregar nuevas columnas permitiendo nulos (`nullable=True`).
2. Modificar el código de Python para escribir en el nuevo formato.
3. Ejecutar un script de backfill asíncrono en lotes pequeños.
4. Eliminar el código legacy y finalmente dropear las columnas viejas en una migración separada.
