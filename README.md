# Olist E-Commerce Data Engineering Project

Proyecto de ingeniería de datos desarrollado en Databricks utilizando el dataset
Brazilian E-Commerce Public Dataset by Olist.

## Objetivo

Construir un pipeline de datos basado en arquitectura Medallion para analizar el ciclo
de pedidos e identificar factores relacionados con retrasos en las entregas y evaluaciones
negativas de los clientes.

## Problemática

Identificar los factores operativos, comerciales y geográficos relacionados con retrasos
en las entregas y una mala experiencia del cliente.

## Tecnologías

- Databricks
- Apache Spark / PySpark
- SQL
- Delta Lake
- Unity Catalog
- Git / GitHub

## Arquitectura

Raw → Bronze → Silver → Gold

![Arquitectura del proyecto Olist](docs/image/Architecture.png)

## Dataset

Brazilian E-Commerce Public Dataset by Olist.

Fuente: Kaggle  
Autor: Olist  
Enlace: https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce

El dataset contiene información sobre pedidos, clientes, vendedores, productos,
pagos, reviews y geolocalización.

## Pipeline

Raw
Datos CSV originales almacenados en un Volume de Databricks.

Bronze
Ingesta de los archivos originales como tablas Delta.

Silver
Limpieza, estandarización, validación de calidad y preparación de entidades.

Gold
Construcción de tablas analíticas y métricas de negocio.

## Principales resultados

- 99.441 pedidos analizados.
- 6,77 % de los pedidos con información de entrega presentaron retraso.
- Tiempo promedio de entrega: 12,5 días.
- Retraso promedio de pedidos tardíos: 10,62 días.
- Pedidos sin retraso: review promedio 4,29.
- Pedidos retrasados: review promedio 2,27.
- Reviews negativas:
  - 9,31 % en pedidos sin retraso.
  - 62,46 % en pedidos retrasados.

Los resultados muestran una fuerte asociación entre retrasos en las entregas
y una peor experiencia del cliente.

## Estructura del repositorio

notebooks/
    00_setup
    01_data_exploration
    02_bronze_ingestion
    03_data_quality_analysis
    04_silver_customers
    05_silver_orders
    06_silver_products
    07_silver_other_tables
    08_gold_business_metrics
    09_delta_lake_tests
    10_optimization

docs/
    ...

## Delta Lake

El proyecto incluye pruebas de:

- Transaction Log
- Time Travel
- UPDATE
- DELETE
- RESTORE
- MERGE
- OPTIMIZE
- ZORDER
- VACUUM

## Autor
**Nicolas Eduardo Rojas Diaz**

- GitHub: [Niicolas-Rojas](https://github.com/Niicolas-Rojas)
- LinkedIn: [Nicolas Eduardo Rojas Diaz](https://www.linkedin.com/in/nicolas-rojass/)
