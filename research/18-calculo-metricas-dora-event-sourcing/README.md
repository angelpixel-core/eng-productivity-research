---
id: 18-calculo-metricas-dora-event-sourcing
title: "¿Cómo calculás métricas de ingeniería (como DORA metrics: Lead Time, Deployment Frequency) garantizando precisión histórica?"
block: "Bloque 4: Big Data Pipelines & Liderazgo Senior"
block_number: 4
question_number: 18
tags:
  - dora-metrics
  - event-sourcing
  - lead-time
  - analytics
  - engineering-productivity
aliases:
  - metricas-dora-event-sourcing
status: documented
created_at: 2026-10-19
has_code_benchmark: false
---

### 18. "¿Cómo calculás métricas de ingeniería (como DORA metrics: Lead Time, Deployment Frequency) garantizando precisión histórica?"

- **Respuesta:**
- Las métricas no se calculan "en caliente" sobre toda la base de datos en cada consulta.
- Se implementa un modelo de **Event Sourcing / Ledger de eventos**: cada commit, apertura de PR, aprobación y release se guarda como un evento inmutable con timestamp UTC.
- Un job programado nocturno o un streaming worker calcula ventanas móviles agregadas (promedios, percentiles p50/p90/p99) y las persiste en tablas de resumen analítico. El dashboard lee datos pre-calculados al instante.
