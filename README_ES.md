# Proyecto de Ingeniería de Datos — Olist E-Commerce

[English version](README.md)

Proyecto práctico de **Ingeniería de Datos** desarrollado en **Databricks** utilizando el **Brazilian E-Commerce Public Dataset by Olist**.

El proyecto implementa un pipeline Lakehouse con arquitectura **Raw → Bronze → Silver → Gold** para transformar archivos CSV originales en tablas Delta validadas y datasets analíticos orientados al análisis del desempeño de entregas y la satisfacción de clientes.

## Objetivo

Construir un pipeline de datos basado en arquitectura Medallion para analizar el ciclo de pedidos e identificar factores asociados con:

- retrasos en las entregas;
- reviews negativas;
- desempeño de entrega;
- satisfacción del cliente.

El proyecto fue desarrollado como parte de mi práctica técnica en Data Engineering, con foco en ingesta, transformación, calidad de datos, modelado, funcionalidades de Delta Lake y generación de datasets analíticos.

## Pregunta de negocio

**¿Cómo se relacionan los retrasos en las entregas con la satisfacción de los clientes dentro del dataset de Olist?**

El análisis es observacional: los resultados muestran asociaciones dentro de los datos históricos y no deben interpretarse como evidencia de causalidad.

## Arquitectura

![Arquitectura Lakehouse de Olist en Databricks](docs/image/Architecture.png)

### Raw

Archivos CSV originales almacenados en un **Databricks Volume**.

### Bronze

Ingesta de los datasets originales como **tablas Delta**, manteniendo la estructura de origen para su procesamiento posterior.

### Silver

Datasets refinados mediante:

- estandarización de tipos de datos;
- limpieza y deduplicación;
- validaciones de calidad;
- controles de integridad referencial;
- controles de coherencia temporal;
- preparación de entidades reutilizables.

### Gold

Tablas analíticas y métricas de negocio preparadas para analizar entregas y satisfacción de clientes.

Principales salidas Gold:

- `order_analysis`
- `delivery_metrics`
- `customer_satisfaction_metrics`
- `delay_severity_metrics`

## Tecnologías

- Databricks
- Apache Spark
- PySpark
- Spark SQL / SQL
- Delta Lake
- Unity Catalog
- Git / GitHub

## Dataset

**Brazilian E-Commerce Public Dataset by Olist**

Fuente: [Kaggle — Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

El dataset contiene información sobre:

- pedidos;
- clientes;
- vendedores;
- productos;
- pagos;
- reviews;
- geolocalización;
- traducciones de categorías de productos.

## Pipeline

```text
Archivos CSV de Olist
        │
        ▼
       RAW
Archivos originales en Databricks Volume
        │
        ▼
     BRONZE
Tablas Delta con datos crudos
        │
        ▼
     SILVER
Limpieza, tipado, validación y entidades refinadas
        │
        ▼
      GOLD
Tablas analíticas y métricas de negocio
```

## Calidad de datos

La capa Silver incorpora controles orientados a mejorar la confiabilidad de los datasets antes de construir las tablas Gold.

Entre ellos:

- estandarización de tipos y valores;
- tratamiento de duplicados;
- revisión de nulos y consistencia;
- validación de integridad referencial;
- validación de coherencia temporal;
- validación de relaciones entre pedidos, clientes, productos, pagos y reviews.

## Principales resultados

El proyecto analizó **99.441 pedidos**.

Principales observaciones:

- **6,77 %** de los pedidos con información de entrega presentaron retraso.
- Tiempo promedio de entrega: **12,5 días**.
- Retraso promedio entre los pedidos tardíos: **10,62 días**.
- Review promedio en pedidos sin retraso: **4,29**.
- Review promedio en pedidos retrasados: **2,27**.
- Reviews negativas en pedidos sin retraso: **9,31 %**.
- Reviews negativas en pedidos retrasados: **62,46 %**.

Los resultados muestran una fuerte asociación entre los retrasos en las entregas y una peor evaluación por parte de los clientes dentro del dataset analizado.

### Reviews negativas según cumplimiento de entrega

```text
Sin retraso:  9,31 %
Con retraso: 62,46 %
```

El análisis detallado de la capa Gold también estudia cómo cambia la proporción de reviews negativas a medida que aumenta la severidad del retraso.

## Funcionalidades de Delta Lake

El proyecto incluye pruebas prácticas de funcionalidades de Delta Lake:

- Transaction Log
- Time Travel
- `UPDATE`
- `DELETE`
- `RESTORE`
- `MERGE`
- `OPTIMIZE`
- `ZORDER`
- `VACUUM`

Estas pruebas fueron utilizadas para comprender conceptos de versionado de tablas, recuperación, actualizaciones incrementales y optimización de almacenamiento y consultas.

## Estructura del repositorio

```text
Brazilian-E-Commerce/
├── Notebooks/
│   ├── 00_setup
│   ├── 01_data_exploration
│   ├── 02_bronze_ingestion
│   ├── 03_data_quality_analysis
│   ├── 04_silver_customers
│   ├── 05_silver_orders
│   ├── 06_silver_products
│   ├── 07_silver_other_tables
│   ├── 08_gold_business_metrics
│   ├── 09_delta_lake_tests
│   └── 10_optimization
│
├── docs/
│   └── image/
│       └── Architecture.png
│
├── README.md
└── README_ES.md
```

## Flujo recomendado de notebooks

Los notebooks siguen el ciclo del pipeline:

1. Configuración del entorno y catálogo.
2. Exploración inicial de los datos.
3. Ingesta Bronze.
4. Análisis de calidad de datos.
5. Transformaciones Silver por entidad.
6. Construcción de tablas y métricas Gold.
7. Pruebas de funcionalidades de Delta Lake.
8. Pruebas de optimización.

## Qué demuestra este proyecto

El proyecto fue desarrollado para practicar y demostrar:

- conceptos de arquitectura Lakehouse y Medallion;
- ingesta de datos con Databricks;
- transformaciones distribuidas con PySpark;
- procesamiento de datos mediante SQL;
- administración de tablas Delta Lake;
- validaciones de calidad de datos;
- modelado relacional;
- construcción de datasets analíticos;
- versionado mediante Git/GitHub;
- transformación de datos crudos en métricas orientadas al negocio.

## Autor

**Nicolás Rojas Díaz**

- GitHub: [Niicolas-Rojas](https://github.com/Niicolas-Rojas)
- LinkedIn: [Nicolás Rojas Díaz](https://www.linkedin.com/in/nicolas-rojass/)
- Portfolio: [niicolas-rojas.github.io](https://niicolas-rojas.github.io/)
