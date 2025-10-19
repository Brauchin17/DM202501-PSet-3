# DM202501-PSet-3

## 1. Arquitectura

| Componente       | Descripción                                                                    |
| ---------------- | ------------------------------------------------------------------------------ |
| Jupyter Notebook | Entorno interactivo para desarrollo, análisis y visualización de datos.        |
| PySpark          | Procesamiento distribuido para ETL y agregaciones sobre grandes volúmenes.     |
| Snowflake        | Data warehouse; esquemas: `RAW` → `ANALYTICS`.                                 |
| Docker Compose   | Orquestación de contenedores para Jupyter/PySpark y persistencia de notebooks. |

### Flujo de datos

`RAW` (Snowflake) → Spark ETL → `Analytics.OBT_TRIPS` (Snowflake) → Notebooks (Docker/Jupyter)

## 2. Matriz de cobertura

| Año  | Taxi   | Ene | Feb | Mar | Abr | May | Jun | Jul | Ago | Sep | Oct | Nov | Dic |
|------|--------|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| 2015 | Yellow | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  |
| 2015 | Green  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  |
| 2016 | Yellow | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  |
| 2016 | Green  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  |
| 2017 | Yellow | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  |
| 2017 | Green  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  |
| 2018 | Yellow | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  |
| 2018 | Green  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  |
| 2019 | Yellow | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  |
| 2019 | Green  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  |
| 2020 | Yellow | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  |
| 2020 | Green  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  |
| 2021 | Yellow | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  |
| 2021 | Green  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  |
| 2022 | Yellow | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  |
| 2022 | Green  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  |
| 2023 | Yellow | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  |
| 2023 | Green  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  |
| 2024 | Yellow | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  |
| 2024 | Green  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  |
| 2025 | Yellow | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  |
| 2025 | Green  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ❌  | ❌  | ❌  | ❌  |

Taxi zones tambien fue subida mediante un csv.

## Pasos para Docker Compose y ejecución de notebooks (orden y parámetros).

1. Clonar repositorio y acceder al proyecto.

2. Crear .env con las variables de Snowflake (ver sección 4).

3. Ejecutar Docker Compose: `docker-compose up -d`

4. Acceder a Jupyter Notebook: `http://localhost:8888/lab`

5. Ejecutar notebooks en orden:

| Notebook         | Propósito                                                    |
| ---------------- | ------------------------------------------------------------ |
| 01_ingesta_parquet_raw      | Lee Parquet 2015–2025 (Yellow/Green) mes a mes|
| 02_enriquecimiento_y_unificacion | Integra Taxi Zones y unifica Yellow/Green                          |
| 03_construccion_obt         | Ensambla analytics.obt_trips                                 |
| 04_validaciones_y_exploracion.      | Valida: nulos, rangos, coherencia de fechas, conteos por mes/servicio |
|05_data_analysis.ipynb|Contesta preguntas de negocio|

## | Variable  | Descripción                |
| --------- | -------------------------- |
| URL       | Endpoint de Snowflake      |
| DB        | Nombre de la base de datos |
| WAREHOUSE | Warehouse de Snowflake     |
| ROLE      | Rol de Snowflake           |
| USER      | Usuario para conexión      |
| PASSWORD  | Contraseña del usuario     |

Guardar el archivo .env en la raíz del proyecto.

## Diseño de `raw` y OBT

### Raw
- Tablas por servicio: Yellow, Green
- Tabla taxi zones y tabla unificada y enriquecida
- Columnas principales: fechas, ubicación pickup/dropoff, tarifa, tipo de servicio, método de pago, distancia, duración.
- Metadatos: `run_id`, `ingested_at_utc`, `source_service`, `source_year`, `source_month`.
- Supuestos: todos los registros tienen fechas de pickup y dropoff válidas; campos obligatorios no nulos

### OBT

Tablas consolidadas, columnas derivadas:
- TRIP_DURATION_MIN (dropoff - pickup)
- AVG_SPEED_MPH (distancia / duración)
- TIP_PCT (tip / fare)
- Metadata: `run_id`, `ingested_at_utc`, `source_service`, `source_year`, `source_month`.
Validaciones: no nulos, rangos coherentes, distancias posibles.

## Calidad/Auditoría

| Validación                           |
| ------------------------------------ | 
| Total de registros        | 
| Nulos     | 
| Conteos por servicio/año/mes         | 
| Distancias fuera de rango | 
| Montos fuera de rango |
| Duraciones de viaje fuera de rango             |
| Pasajeros fuera de rango|
| Maximos y minimo|

## Checklist

- [x] Docker Compose levanta **Spark** y **Jupyter Notebook** correctamente.
- [x] Todas las credenciales y parámetros provienen de **variables de ambiente** (`.env`).
- [x] Cobertura **2015–2025 (Yellow/Green)** cargada en RAW, con **matriz de cobertura** y **conteos por lote**.
- [x] `analytics.obt_trips` creada con **columnas mínimas**, derivadas y metadatos.
- [x] **Idempotencia** verificada reingestando al menos un mes.
- [x] Validaciones básicas documentadas:
  - Nulos
  - Rangos
  - Coherencia de fechas y distancias
- [x] **20 preguntas de análisis** respondidas usando la OBT (texto y resultados).
- [x] **README completo**: pasos de ejecución, variables, esquema, decisiones y troubleshooting.




