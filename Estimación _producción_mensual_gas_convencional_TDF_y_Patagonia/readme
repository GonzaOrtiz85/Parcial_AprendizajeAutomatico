# Proyecto parcial de Aprendizaje Automático

## Estimación de la producción mensual de gas convencional en provincias patagónicas

**Alumno:** Gonzalo Ortiz
**Materia:** Aprendizaje Automático
**Proyecto:** Trabajo integrador parcial

**Documentación del proyecto**
- [Formulación del problema](reports/formulacion_del_problema.md)
- [Descripción del dataset](reports/descripcion_del_dataset.md)
- [Modelo y resultados](reports/modelo_y_resultados.md)

---

## Descripción general del proyecto

Este proyecto propone aplicar técnicas de Aprendizaje Automático para estimar la producción mensual de gas convencional en provincias patagónicas productoras, manteniendo a Tierra del Fuego como caso principal de análisis.

En una primera formulación, el trabajo estaba pensado únicamente sobre Tierra del Fuego. Sin embargo, al revisar el dataset se observó que ese recorte dejaba una cantidad limitada de registros para entrenar modelos. Por ese motivo, se amplió el enfoque a un recorte regional integrado por Tierra del Fuego, Santa Cruz, Chubut, Río Negro y Neuquén.

El objetivo sigue siendo analizar la producción mensual de gas convencional, pero con una base de datos más amplia y adecuada para construir modelos de regresión.

---

## Objetivo del proyecto

Aplicar modelos de Aprendizaje Automático para estimar la producción mensual de gas convencional a partir de variables temporales, territoriales y valores históricos de producción.

---

## Tipo de problema

El proyecto corresponde a un problema de **regresión**, ya que la variable objetivo es numérica y continua.

La variable objetivo es:

`cantidad_mm3`

Esta columna representa la producción mensual de gas convencional medida en millones de metros cúbicos.

---

## Dataset utilizado

El dataset utilizado proviene del portal **Datos Argentina**, a partir del conjunto:

**Producción de Petróleo y Gas SESCO**

Recurso utilizado:

**Producción gas SESCO más Tight y Shale capítulo IV por provincia**

El archivo original se encuentra en formato CSV y contiene información mensual sobre producción de gas por provincia y tipo de concepto.

---

## Recorte aplicado

Para el desarrollo del proyecto se aplicó el siguiente recorte:

* Concepto: `Producción convencional`
* Provincias seleccionadas:

  * Tierra del Fuego
  * Santa Cruz
  * Chubut
  * Rio Negro
  * Neuquén

Este recorte permite mantener el interés local sobre Tierra del Fuego, pero con una base regional más robusta para trabajar con modelos de Aprendizaje Automático.

---

## Características del dataset

El archivo original contiene:

* 7494 filas
* 6 columnas
* Frecuencia mensual
* Período: enero de 2009 a abril de 2026

Columnas originales:

* `anio`
* `mes`
* `indice_tiempo`
* `provincia`
* `concepto`
* `cantidad_mm3`

Luego del recorte y del preprocesamiento inicial, el dataset final preparado para Machine Learning quedó conformado por:

* 1025 filas
* 10 columnas

Columnas finales:

* `anio`
* `mes`
* `indice_tiempo`
* `provincia`
* `concepto`
* `cantidad_mm3`
* `produccion_mes_anterior`
* `produccion_dos_meses_antes`
* `promedio_3_meses`
* `variacion_mes_anterior`

---

## Variables construidas

Para adaptar el dataset a un problema de Aprendizaje Automático, se construyeron variables históricas por provincia:

* `produccion_mes_anterior`
* `produccion_dos_meses_antes`
* `promedio_3_meses`
* `variacion_mes_anterior`

Estas variables permiten que el modelo utilice información de meses anteriores para estimar la producción mensual.

---

## Entrega 1

La Entrega 1 corresponde a la **descripción y formulación del objetivo del proyecto**.

Incluye:

* Tema del proyecto
* Contexto del problema
* Relevancia del tema
* Tipo de problema
* Variable objetivo
* Variables predictoras posibles
* Modelos posibles
* Métricas previstas
* Alcance inicial del trabajo

Archivo sugerido:

`reports/entrega_1_descripcion_objetivo.pdf`

---

## Entrega 2

La Entrega 2 corresponde a la **descripción del dataset y su origen**.

Incluye:

* Origen del dataset
* Fuente de datos
* Descripción del archivo original
* Cantidad de instancias
* Características y columnas
* Tipos de datos
* Recorte aplicado
* Preprocesamiento inicial
* Dataset final preparado
* Archivos incluidos en el repositorio

Archivo sugerido:

`reports/entrega_2_dataset_origen.pdf`

---

## Estructura del repositorio

```text
parcial_producciongas/
│
├── data/
│   ├── raw/
│   │   └── dataset_original.csv
│   │
│   └── processed/
│       └── produccion_gas_patagonia_ml.csv
│
├── notebooks/
│   └── 01_exploracion_dataset_gas.ipynb
│
├── reports/
│   ├── entrega_1_descripcion_objetivo.pdf
│   └── entrega_2_dataset_origen.pdf
│
├── src/
│
├── models/
│
├── README.md
└── requirements.txt
```

---

## Herramientas utilizadas

* Python
* Google Colab
* pandas
* scikit-learn
* GitHub
* Datos Argentina

---

## Próximos pasos

En la siguiente etapa del proyecto se avanzará con:

* Entrenamiento de modelos de regresión
* Evaluación con métricas como MAE, RMSE y R2
* Análisis de resultados con foco en Tierra del Fuego

---

## Referencias

* Datos Argentina. Producción de Petróleo y Gas SESCO.
* Secretaría de Energía de la Nación.
* Programa de la materia Aprendizaje Automático 2026.
