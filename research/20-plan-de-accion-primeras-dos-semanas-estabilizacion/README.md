---
id: 20-plan-de-accion-primeras-dos-semanas-estabilizacion
title: "Llegas a un proyecto interno existente y ves que los prototipos son inestables y lentos. ¿Cuál es tu plan de acción en las primeras dos semanas?"
block: "Bloque 4: Big Data Pipelines & Liderazgo Senior"
block_number: 4
question_number: 20
tags:
  - stabilization
  - observability
  - opentelemetry
  - testing
  - staff-strategy
  - roadmap
aliases:
  - plan-de-accion-primeras-dos-semanas
status: documented
created_at: 2026-10-19
has_code_benchmark: false
---

### 20. "Llegas a un proyecto interno existente y ves que los prototipos son inestables y lentos. ¿Cuál es tu plan de acción en las primeras dos semanas?"

- **Respuesta:**

1. **Semana 1 (Observabilidad & Diagnóstico):** Antes de refactorizar una sola línea, configuro trazas distribuidas (OpenTelemetry / AWS X-Ray), CloudWatch y Sentry. Identifico los endpoints con mayor p99 de latencia y los puntos de fallo más frecuentes.
2. **Contratos y tests mínimos:** Escribo tests de integración en los flujos críticos de ingesta y autenticación para tener una red de seguridad contra regresiones.
3. **Semana 2 (Estabilización pragmática):** Elimino bloqueos síncronos en APIs, configuro pools de conexión adecuados hacia Aurora/Redis y desacoplo las llamadas a LLMs a tareas en segundo plano. Entrego estabilidad demostrable con métricas antes de sumar nuevas features.
