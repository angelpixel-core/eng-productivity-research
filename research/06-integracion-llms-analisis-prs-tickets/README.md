---
id: 06-integracion-llms-analisis-prs-tickets
title: "¿Cómo integras LLMs en un backend Python para analizar Pull Requests o tickets sin reventar los costos de tokens ni los timeouts?"
block: "Bloque 2: Integración de IA/LLMs y Flujos Productivos"
block_number: 2
question_number: 6
tags:
  - llm
  - structured-outputs
  - pydantic
  - pr-analysis
  - finops
  - tokens
aliases:
  - integracion-llms-backend
status: documented
created_at: 2026-10-19
has_code_benchmark: false
---

### 6. "¿Cómo integras LLMs en un backend Python para analizar Pull Requests o tickets sin reventar los costos de tokens ni los timeouts?"

- **Respuesta:**

1. **Filtrado previo determinista (Chunking & Pruning):** Nunca enviar un diff completo de Git al modelo sin procesar. Filtro archivos de dependencias (`lockfiles`, binarios, minificados) y paso solo los fragmentos contextuales o el árbol de cambios sintácticos (AST).
2. **Contratos estructurados:** Uso la API de Structured Outputs / JSON Schema con Pydantic para garantizar que la respuesta del LLM se serialice directamente a un DTO de métricas sin parsing frágil de strings.
3. **Caché semántica o determinista:** Si dos desarrolladores envían el mismo snippet o la misma consulta estándar, verifico un hash en Redis antes de disparar la llamada al proveedor.
4. **Procesamiento desacoplado:** Toda inferencia pesada corre en background (worker asíncrono o Lambda), notificando el resultado al webhook del repositorio cuando finaliza.
