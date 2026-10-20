---
id: 09-control-contexto-ventana-tokens-map-reduce
title: "¿Cómo manejas el control de contexto y la ventana de tokens al resumir el historial de sprints o repositorios completos?"
block: "Bloque 2: Integración de IA/LLMs y Flujos Productivos"
block_number: 2
question_number: 9
tags:
  - llm
  - map-reduce
  - context-window
  - summarization
  - tokens
aliases:
  - control-contexto-tokens-map-reduce
status: documented
created_at: 2026-10-19
has_code_benchmark: false
---

### 9. "¿Cómo manejas el control de contexto y la ventana de tokens al resumir el historial de sprints o repositorios completos?"

- **Respuesta:**
  Aplico técnicas de **Map-Reduce o Refine jerárquico**:
- **Fase Map:** Divido el historial por PR o por módulo de código. El LLM resume y extrae riesgos clave de cada fragmento individual.
- **Fase Reduce:** Agrupo los resúmenes sintéticos generados en un único prompt consolidado para extraer el reporte final de productividad del equipo.
- Esto previene que se diluya la atención del modelo y permite paralelizar las llamadas de la fase Map.
