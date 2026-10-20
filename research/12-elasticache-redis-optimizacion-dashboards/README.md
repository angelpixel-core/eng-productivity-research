---
id: 12-elasticache-redis-optimizacion-dashboards
title: "¿Cómo integras ElastiCache (Redis) para optimizar consultas pesadas de dashboards?"
block: "Bloque 3: AWS, Bases de Datos & Arquitectura Cloud"
block_number: 3
question_number: 12
tags:
  - redis
  - elasticache
  - caching
  - cache-aside
  - redlock
  - dashboards
aliases:
  - elasticache-redis-dashboards
status: documented
created_at: 2026-10-19
has_code_benchmark: false
---

### 12. "¿Cómo integras ElastiCache (Redis) para optimizar consultas pesadas de dashboards?"

- **Respuesta:**
- **Estrategia Cache-Aside:** La API consulta primero la clave en Redis (`team:{id}:dora_metrics:weekly`). Si hay _Cache Miss_, consulta la base de datos Aurora, procesa los datos, escribe en Redis con un TTL (Time To Live) prudente (ej. 15 minutos) y responde al cliente.
- **Invalidación reactiva:** Si entra un webhook de despliegue en producción, se purga la clave de métricas del equipo correspondiente para forzar el recálculo en la siguiente lectura.
- **Locks distribuidos:** Si 10 requests concurrentes intentan calcular el mismo reporte pesado al expirar el caché, uso un lock en Redis (`Redlock` o `SET NX EX`) para que un solo worker haga el cálculo mientras los demás esperan.
