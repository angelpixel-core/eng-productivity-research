---
id: 14-diseno-dynamodb-hot-partitions-write-sharding
title: "¿Cómo diseñás una tabla en DynamoDB para evitar particiones calientes (Hot Partitions) al recibir millones de eventos?"
block: "Bloque 3: AWS, Bases de Datos & Arquitectura Cloud"
block_number: 3
question_number: 14
tags:
  - aws
  - dynamodb
  - hot-partitions
  - write-sharding
  - nosql
  - scalability
aliases:
  - dynamodb-write-sharding
status: documented
created_at: 2026-10-19
has_code_benchmark: false
---

### 14. "¿Cómo diseñás una tabla en DynamoDB para evitar particiones calientes (Hot Partitions) al recibir millones de eventos?"

- **Respuesta:**
- El problema ocurre si todos los eventos escriben bajo la misma Partition Key (PK), por ejemplo `DATE#2026-10-13`, saturando la capacidad de la partición física (límite de 1000 WCU / 3000 RCU).
- **Solución (Write Sharding / Salt):** Agregar un sufijo aleatorio o calculado a la clave de partición: `PK: ORG#123#METRICS_2026-10-13#SHARD_{0-9}`.
- Al escribir, se distribuye la carga entre los 10 shards. Al leer un reporte agregado, se realizan lecturas paralelas distribuidas sobre cada shard.
