---
id: 08-evaluacion-consistencia-evitar-alucinaciones-metricas-ia
title: "¿Cómo evaluás la consistencia y evitas alucinaciones cuando la IA genera métricas de código?"
block: "Bloque 2: Integración de IA/LLMs y Flujos Productivos"
block_number: 2
question_number: 8
tags:
  - llm
  - hallucinations
  - guardrails
  - few-shot
  - pydantic
  - data-quality
aliases:
  - consistencia-alucinaciones-ia
status: documented
created_at: 2026-10-19
has_code_benchmark: false
---

### 8. "¿Cómo evaluás la consistencia y evitas alucinaciones cuando la IA genera métricas de código?"

- **Respuesta:**
- **Separación de roles:** La IA **no calcula** métricas matemáticas (como cantidad de líneas cambiadas o tiempo de compilación); eso lo calcula código determinista en Python. La IA se utiliza para tareas de clasificación, resumen y análisis cualitativo (ej. "detectar si este commit introduce riesgo arquitectónico o falta de tests").
- **Few-shot examples:** Incluir ejemplos concretos en el system prompt con casos válidos e inválidos.
- **Validación post-inferencia:** Si el modelo genera un payload JSON, pasa por validación estricta de Pydantic. Si falla la validación de tipos o rangos, se rechaza y reintenta con un prompt de corrección.
