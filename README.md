**Estimación de la producción mensual de gas convencional en Tierra del Fuego y provincias patagónicas**

**Realizado por el alumno:** Gonzalo Ortiz 
**Docente** : Nicolás Caballero 
**Materia**: Aprendizaje Automático 
**Proyecto**: Proyecto parcial de Aprendizaje Automático

**Link del vídeo presentación**: https://youtu.be/7qnsR92DdLY

**Reportes claves del proyecto**

Formulación del problema: informes/formulacion_del_problema.md
Descripción del conjunto de datos: informes/descripcion_del_dataset.md
Modelo y resultados: informes/modelo_y_resultados.md

**Descripción general del proyecto**
Este proyecto propone aplicar técnicas de Aprendizaje Automático para estimar la producción mensual de gas convencional en provincias patagónicas productoras, manteniendo a Tierra del Fuego como caso principal de análisis.

En una primera formulación, el trabajo estaba pensado únicamente sobre Tierra del Fuego. Sin embargo, al revisar el conjunto de datos se comprobará que ese recorte dejaba una cantidad limitada de registros para entrenar modelos. Por ese motivo, se amplió el enfoque a un recorte regional integrado por Tierra del Fuego, Santa Cruz, Chubut, Río Negro y Neuquén.

El objetivo sigue siendo analizar la producción mensual de gas convencional, pero con una base de datos más amplia y adecuada para construir modelos de regresión.

**Objetivo del proyecto**
Aplique modelos de Aprendizaje Automático para estimar la producción mensual de gas convencional a partir de variables temporales, territoriales y valores históricos de producción.

**Tipo de problema**
El proyecto corresponde a un problema de regresión , ya que la variable objetivo es numérica y continua.

**La variable objetivo es:**

cantidad_mm3

Esta columna representa la producción mensual de gas convencional medida en millones de metros cúbicos.

Conjunto de datos utilizado
El conjunto de datos utilizado proviene del portal Datos Argentina , a partir del conjunto:

Producción de Petróleo y Gas SESCO

Recurso utilizado:

Producción gas SESCO más Tight y Shale capítulo IV por provincia

El archivo original se encuentra en formato CSV y contiene información mensual sobre producción de gas por provincia y tipo de concepto.

Corte aplicado
Para el desarrollo del proyecto se aplicó el siguiente recorte:

Concepto:Producción convencional

Provincias seleccionadas:

Tierra del Fuego
Santa Cruz
Chubut
Río Negro
Neuquén

Este recorte permite mantener el interés local sobre Tierra del Fuego, pero con una base regional más robusta para trabajar con modelos de Aprendizaje Automático.

Características del conjunto de datos
El archivo original contiene:

7494 filas
6 columnas
Frecuencia mensual
Período: enero de 2009 a abril de 2026
Columnas originales:

anio
mes
indice_tiempo
provincia
concepto
cantidad_mm3

Luego del recorte y del preprocesamiento inicial, el conjunto de datos final preparado para Machine Learning quedó conformado por:

1025 filas
10 columnas

Columnas finales:

anio
mes
indice_tiempo
provincia
concepto
cantidad_mm3
produccion_mes_anterior
produccion_dos_meses_antes
promedio_3_meses
variacion_mes_anterior
Variables construidas

Para adaptar el conjunto de datos a un problema de Aprendizaje Automático, se construyeron variables históricas por provincia:

produccion_mes_anterior
produccion_dos_meses_antes
promedio_3_meses
variacion_mes_anterior
Estas variables permiten que el modelo utilice información de meses anteriores para estimar la producción mensual.

**Entrega 1**
Archivo: formulacion_objetivo.md

La Entrega 1 corresponde a la descripción y formulación del objetivo del proyecto .

Incluye:

Tema del proyecto
Contexto del problema
Relevancia del tema
Tipo de problema
Variable objetivo
Variables predictoras posibles
Modelos posibles
Métricas previstas
Alcance inicial del trabajo

**Entrega 2**
Archivo:reports/descripcion_dataset_origen.md

La Entrega 2 corresponde a la descripción del conjunto de datos y su origen .

Incluye:

Origen del conjunto de datos
Fuente de datos
Descripción del archivo original
Cantidad de instancias
Características y columnas
Tipos de datos
Corte aplicado
Preprocesamiento inicial
Conjunto de datos final preparado
Archivos incluidos en el repositorio

**tercera entrega:**
Archivo: modelos_y_resultados.md

En esta etapa del proyecto avanza con:

Entrenamiento de modelos de regresión
Evaluación con métricas como MAE, RMSE y R2

Análisis de resultados con foco en Tierra del Fuego

**Estructura del repositorio**
parcial_producciongas/
│
├── data/
│   ├── raw/
│   │   └── dataset_original.csv
│   │
│   └── processed/
│       └── produccin-gas-sesco-tight-y-shale-captulo-iv-por-provincia.csv
│
├── notebooks/
│   └── parcial_producciongas.ipynb
│
├── reports/
│   ├── descripcion_dataset_origen.md
│   ├── formulacion_objetivo.md
│   └── modelos_y_resultados.md
│
├── src/
│
├── models/
│
├── README.md
└── requirements.txt

**Herramientas utilizadas**

Pitón
Google Colab
pandas
scikit-learn
GitHub
Sitio Datos Argentina

Referencias
Datos argentinos. Producción de Petróleo y Gas SESCO.
Secretaría de Energía de la Nación.
Material bibliográfico y Programa de la materia Aprendizaje Automático 2026.
