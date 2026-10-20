---
id: 01-como-encarar-profiling-y-optimizacion
title: "¿Cómo encaras el profiling y optimización de un servicio Python que consume demasiada CPU o memoria procesando métricas de ingeniería?"
block: "Bloque 1: Python Profiling, Optimización & Performance"
block_number: 1
question_number: 1
tags:
  - python
  - profiling
  - py-spy
  - tracemalloc
  - memray
  - slots
  - performance
aliases:
  - python-profiling-optimizacion
status: documented
created_at: 2026-10-19
has_code_benchmark: true
---

# 1. "¿Cómo encaras el profiling y optimización de un servicio Python que consume demasiada CPU o memoria procesando métricas de ingeniería?"

### Respuesta:

- **Evito adivinar:** Uso herramientas de profiling sin instrumentación invasiva como `py-spy` (toma muestras del stack trace en tiempo de ejecución con overhead menor al 1%) para generar un flamegraph e identificar funciones "calientes" en CPU.

- **Análisis de memoria:** Si hay picos o leaks, utilizo `tracemalloc` o `memray` para detectar dónde se retienen objetos grandes (ej. DataFrames o árboles de AST de código sin liberar).

- **Optimización algorítmica y estructuras:** Sustituyo bucles de parsing con generadores perezosos (`yield`), uso `__slots__` en clases masivas de eventos para reducir el overhead de diccionarios internos en un 40-50%, o delego la computación vectorial a librerías compiladas en C/Rust (`polars`, `numpy`).

---

### Benchmark Práctico

Este módulo incluye un script ejecutable demostrativo: [`benchmark_engineering_metrics.py`](./benchmark_engineering_metrics.py).
Simula la saturación de memoria y cuellos de botella de CPU al procesar eventos de commits masivos, comparando la implementación sin optimizar frente al uso de `__slots__` y algoritmos $O(n)$ optimizados.
