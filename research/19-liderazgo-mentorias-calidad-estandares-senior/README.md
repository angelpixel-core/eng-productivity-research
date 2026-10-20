---
id: 19-liderazgo-mentorias-calidad-estandares-senior
title: "Como Senior, ¿cómo guías a ingenieros menos experimentados en el equipo para mantener la calidad y estándares?"
block: "Bloque 4: Big Data Pipelines & Liderazgo Senior"
block_number: 4
question_number: 19
tags:
  - leadership
  - code-reviews
  - adrs
  - mentorship
  - standards
  - ci-cd
aliases:
  - liderazgo-calidad-estandares
status: documented
created_at: 2026-10-19
has_code_benchmark: false
---

### 19. "Como Senior, ¿cómo guías a ingenieros menos experimentados en el equipo para mantener la calidad y estándares?"

- **Respuesta:**
- **Automatización en el pipeline (CI/CD):** No gasto tiempo de code review discutiendo formato o linters. Obligo el cumplimiento de `ruff`, `mypy` y suites de tests en pre-commit y GitHub Actions.
- **Code Reviews formativos:** En lugar de solo marcar errores, explico el _trade-off_ arquitectónico: _"Si hacemos esta llamada síncrona dentro del bucle, generamos $N+1$ requests a la base. ¿Cómo podemos resolverlo con una precarga o un batch?"_
- **Documentación viva y ADRs:** Registro decisiones complejas mediante _Architecture Decision Records_ (ADRs) para que el equipo entienda el porqué de una elección tecnológica y no solo el código resultante.
