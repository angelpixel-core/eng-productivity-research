---
id: 17-pipelines-big-data-telemetria-cicd-polars-duckdb-spark
title: "¿Qué experiencia tenés con pipelines de Big Data en Python y cómo procesarías gigabytes de telemetría de CI/CD?"
block: "Bloque 4: Big Data Pipelines & Liderazgo Senior"
block_number: 4
question_number: 17
tags:
  - big-data
  - polars
  - duckdb
  - spark
  - parquet
  - s3
  - telemetry
aliases:
  - big-data-telemetria-cicd
status: documented
created_at: 2026-10-19
has_code_benchmark: false
---

### 17. "¿Qué experiencia tenés con pipelines de Big Data en Python y cómo procesarías gigabytes de telemetría de CI/CD?"

- **Respuesta:**
- En lugar de procesar archivos gigantes en memoria con Pandas (que dispara errores OOM), recurro a procesamiento distribuido o en streaming:
- **Nivel motor:** Uso de **Apache Spark (AWS EMR o Dataproc)** o engines locales de alto rendimiento como **Polars / DuckDB** para consultas analíticas sobre archivos en formato **Parquet** particionados por fecha en S3.
- **Almacenamiento columnar:** Guardar datos en Parquet reduce los costos de almacenamiento hasta un 80% y permite que las consultas escaneen únicamente las columnas relevantes (proyección) sin leer todo el disco.
