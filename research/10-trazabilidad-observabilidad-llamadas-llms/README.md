---
id: 10-trazabilidad-observabilidad-llamadas-llms
title: "¿Cómo aseguras la trazabilidad y observabilidad de las llamadas a LLMs en un entorno productivo?"
block: "Bloque 2: Integración de IA/LLMs y Flujos Productivos"
block_number: 2
question_number: 10
tags:
  - observability
  - opentelemetry
  - cloudwatch
  - finops
  - metrics
  - tracing
aliases:
  - observabilidad-llamadas-llms
status: documented
created_at: 2026-10-19
has_code_benchmark: false
---

### 10. "¿Cómo aseguras la trazabilidad y observabilidad de las llamadas a LLMs en un entorno productivo?"

- **Respuesta:**
  Implemento un sistema de telemetría que registra por cada invocación:
- Tokens de entrada, tokens de salida y costo calculado en centavos de dólar.
- Latencia de Time-to-First-Token y tiempo total de respuesta.
- Correlation ID asociado al commit o usuario que disparó la acción.
- Registro de fallos de rate limiting (códigos 429) exportados a **AWS CloudWatch** para alertar saturación de cuotas.
