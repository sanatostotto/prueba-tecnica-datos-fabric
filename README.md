Clonar repo / ejecutar con el compilador de confianza

Ejecutar el notebook y hacer commit con sus respuestas.

Prueba Técnica – Especialista de Datos

Microsoft Fabric • Spark • SQL • Power BI • Retail (POS & Ventas)

Este repositorio contiene el material necesario para resolver la prueba técnica del rol Especialista de Datos / Data Engineer – Microsoft Fabric.
El examen simula un entorno real de retail (ventas POS), evaluando capacidades técnicas en:

SQL analítico

Spark (PySpark)

Transformaciones tipo Medallion

Limpieza y agregación de datos

Manipulación de DataFrames

Joins, ranking, funciones ventana

Buenas prácticas de ingeniería

Objetivo de la prueba

Evaluar tu capacidad para procesar, analizar y transformar datos de un sistema real utilizando herramientas compatibles con Microsoft Fabric, SQL y Spark.

La prueba también mide:

Pensamiento analítico

Buenas prácticas de código

Claridad en consultas SQL

Correcto uso de DataFrames

Lectura y escritura de datos

Dominio del modelo retail básico

Tipo de prueba

Esta es una prueba práctica guiada, dividida en dos bloques:

Retos SQL (usando spark.sql)
Evalúa joins, agregaciones, funciones ventana, lógica analítica y modelado básico.

Retos Spark (API de DataFrames)
Evalúa lógica de ingeniería, creación de columnas, UDF, agregaciones y estilo Medallion.

Estructura del repositorio

/
├─ README.md
├─ prueba_tecnica_fabric_spark_sql.ipynb
└─ data/
   ├─ products.csv
   ├─ stores.csv
   ├─ sales.csv
   └─ inventory.csv

Data Sheets (Diccionario de Datos)

A continuación se describe la estructura de cada archivo del directorio /data:

products.csv
Catálogo de productos.

Columnas:

product_id: Identificador único del producto

name: Nombre comercial

category: Categoría (Mochilas, Eco, Accesorios, etc.)

cost: Costo unitario

price: Precio de venta

Uso típico:

Joins con ventas

Atributos descriptivos

Transformaciones con UDF

stores.csv
Listado de tiendas presenciales + tienda online.

Columnas:

store_id: Identificador único

name: Nombre de tienda

city: Ciudad

region: Macrozona o región

Uso típico:

Ranking por región

Segmentación geográfica

Joins con ventas

sales.csv
Histórico de ventas POS y online.

Columnas:

sale_id: Identificador único de venta

sale_date: Fecha de venta

product_id: Producto vendido

store_id: Tienda donde ocurrió la venta

quantity: Cantidad vendida

unit_price: Precio unitario en la venta

Uso típico:

Cálculo de total vendido

Ranking

Aggregations

Silver tables

inventory.csv
Inventario por tienda y producto.

Columnas:

product_id: Producto

store_id: Tienda

stock: Unidades disponibles

Uso típico:

Validaciones cruzadas

Preparación de modelos retail

Notebook de la prueba

El archivo prueba_tecnica_fabric_spark_sql.ipynb contiene:

Carga automática de los datasets

Creación de vistas temporales en Spark

3 retos SQL

2 retos Spark

Celdas preparadas con TODO para escribir tus respuestas

Tiempo estimado

Duración sugerida: 60–90 minutos.

Requisitos técnicos

Python 3

Spark disponible (Fabric Notebooks, Databricks, local PySpark, Codespaces o similar)

Capacidad para ejecutar spark.sql

Lectura de archivos CSV

Entrega final

El candidato debe entregar:

Un repositorio en GitHub / Azure DevOps con:

El notebook resuelto

Cualquier artefacto adicional (si aplica)

El enlace del repositorio será entregado en el formulario oficial de la prueba.

Buenas prácticas sugeridas

Mantén SQL claro y organizado

Usa alias descriptivos

Documenta pasos dentro del notebook

Evita código muerto

Asegura que cada celda produce salida válida

Produce resultados limpios y fáciles de entender

¡Éxitos!

Esta prueba está diseñada para evaluar tu claridad técnica, tu capacidad de análisis y la calidad de tus soluciones más que memorizar sintaxis.