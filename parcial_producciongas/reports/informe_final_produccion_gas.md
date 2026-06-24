# Estimación de la producción mensual de gas convencional en Tierra del Fuego y provincias patagónicas

## Entrega 1: Descripción y formulación del objetivo

### Descripción del proyecto

Este proyecto propone aplicar modelos de Aprendizaje Automático supervisado para estimar la producción mensual de gas convencional en Tierra del Fuego y otras provincias patagónicas productoras.

La idea central es trabajar con datos históricos oficiales de producción hidrocarburífera y analizar si variables temporales, provinciales y valores de producción de meses anteriores pueden servir para aproximar la producción de un mes determinado.

El trabajo se enfoca en la producción convencional de gas. En el caso de Tierra del Fuego, esta actividad tiene relevancia por su vínculo con la Cuenca Austral, la producción offshore, las regalías provinciales, el empleo, la infraestructura energética y el abastecimiento de gas natural dentro de la matriz energética nacional.

### Contexto del problema

Tierra del Fuego tiene una relación histórica con la producción de hidrocarburos. Dentro de esa actividad, el gas natural ocupa un lugar importante por la presencia de áreas de producción ubicadas tanto en tierra como costa afuera.

La producción de gas forma parte de una cadena productiva más amplia. Primero se encuentra la etapa de exploración y producción, donde las empresas operadoras extraen el recurso. Luego aparece el tratamiento del gas en plantas ubicadas principalmente en la zona norte de la isla y finalmente su transporte hacia el sistema nacional, mediante infraestructura conectada al Gasoducto San Martín.

En Tierra del Fuego conviven operaciones onshore y offshore. Las primeras se desarrollan en tierra, mientras que las segundas se realizan costa afuera. Esta característica le da a la producción gasífera fueguina una dimensión técnica, logística y económica importante.

El problema resulta relevante porque permite aplicar Aprendizaje Automático a un tema vinculado con la producción energética regional. Además, se trabaja con datos reales, públicos y oficiales, lo que permite evitar una variable objetivo artificial. La producción mensual de gas convencional es un dato registrado, medible y comparable en el tiempo.

Desde el punto de vista del Aprendizaje Automático, la producción mensual de gas convencional puede analizarse como una variable numérica observada a lo largo del tiempo. Por ese motivo, el problema se formula como una tarea de regresión.

### Problema que se abordará

El problema que se abordará es la estimación de la producción mensual de gas convencional a partir del comportamiento histórico de la serie de producción.

La pregunta orientadora del proyecto es:

**¿Es posible estimar la producción mensual de gas convencional en Tierra del Fuego y provincias patagónicas utilizando variables temporales, provinciales y valores históricos de producción?**

### Tipo de problema

El proyecto se plantea como un problema de **regresión**, porque la variable objetivo es numérica.

El valor que se buscará estimar será la producción mensual de gas convencional, medida en millones de metros cúbicos.

No se trata de un problema de clasificación, ya que el objetivo no es asignar categorías, sino predecir un valor continuo de producción.

### Variable objetivo

La variable objetivo será:

`cantidad_mm3`

Esta columna representa la producción mensual de gas medida en millones de metros cúbicos.

El modelo intentará estimar esta variable a partir de información temporal, provincial y de valores históricos de producción.

### Variables predictoras posibles

Las variables predictoras estarán relacionadas con el comportamiento temporal y territorial de la producción. Entre ellas se podrán utilizar:

* Año.
* Mes.
* Provincia.
* Producción del mes anterior.
* Producción de dos meses anteriores.
* Promedio de producción de los últimos tres meses.
* Variación respecto de meses anteriores.

Estas variables podrán ajustarse durante la etapa de preprocesamiento, según la calidad de los datos y los resultados del análisis exploratorio.

### Objetivo general

Aplicar modelos de Aprendizaje Automático supervisado para estimar la producción mensual de gas convencional en Tierra del Fuego y provincias patagónicas a partir de datos históricos oficiales de producción.

### Objetivos específicos

* Describir el contexto productivo del gas natural en Tierra del Fuego y provincias patagónicas.
* Identificar una fuente oficial de datos sobre producción de gas.
* Filtrar y preparar los registros correspondientes a producción convencional de gas.
* Realizar un análisis exploratorio del dataset mediante medidas descriptivas y gráficos.
* Preparar el dataset mediante limpieza, selección de variables y creación de variables temporales e históricas.
* Entrenar modelos de regresión utilizando Python y scikit-learn.
* Evaluar los modelos mediante métricas de regresión como MAE, RMSE y R2.
* Comparar los resultados obtenidos entre los modelos utilizados.
* Elaborar conclusiones sobre el desempeño de los modelos y sus principales limitaciones.

### Modelos posibles

Para abordar el problema se podrán utilizar modelos supervisados de regresión vistos o relacionados con los contenidos de la materia.

**Regresión lineal**

Será utilizada como modelo base. Permitirá observar si las variables temporales e históricas permiten aproximar la producción mensual de gas convencional.

**K vecinos más cercanos para regresión**

Este modelo permitirá estimar valores a partir de registros con características similares. Se relaciona con el contenido de KNN trabajado en la materia.

**Árbol de decisión para regresión**

Este modelo permitirá construir reglas de decisión y captar relaciones que no necesariamente sean lineales.

**Random Forest Regressor**

De manera opcional, se podrá incorporar un modelo de ensamble como comparación adicional. No será el modelo principal, sino una referencia para observar si mejora los resultados respecto de modelos más simples.

### Métricas de evaluación previstas

Al tratarse de un problema de regresión, se utilizarán métricas adecuadas para evaluar errores en valores numéricos.

**MAE**

El error absoluto medio permite conocer el error promedio de predicción en la misma unidad de la producción.

**RMSE**

La raíz del error cuadrático medio penaliza más los errores grandes, por lo que permite observar si el modelo comete errores importantes en algunos meses.

**R2**

El coeficiente de determinación permite observar qué parte de la variación de la producción logra explicar el modelo.

### Resultados esperados

Se espera que los modelos puedan captar parte del comportamiento histórico de la producción mensual de gas convencional, especialmente a partir de la producción de meses anteriores y de variables temporales como mes y año.

El modelo no buscará explicar completamente el comportamiento del sector gasífero, ya que el dataset no incluye todos los factores que pueden afectar la producción, como precios, inversiones, mantenimiento de instalaciones, decisiones empresariales, entrada de nuevos pozos o cambios regulatorios.

---

## Entrega 2: Descripción del dataset

### Dataset seleccionado

Para este proyecto se utilizará el dataset **Producción gas SESCO más Tight y Shale capítulo IV por provincia**, publicado en el portal **Datos Argentina** y proveniente de registros oficiales de la Secretaría de Energía de la Nación.

El archivo se encuentra en formato CSV y contiene información histórica sobre la producción mensual de gas por provincia, tipo de producción y período de tiempo.

La elección de este dataset responde a que se trata de una fuente pública, oficial y de dominio abierto, lo que permite trabajar con datos reales y verificables para un proyecto de Aprendizaje Automático.

### Origen de los datos

Los datos provienen del portal Datos Argentina, dentro del conjunto de datos vinculado a la producción de petróleo y gas publicada por la Secretaría de Energía de la Nación.

La descarga del dataset se realizó durante junio de 2026 para su uso en el proyecto de Aprendizaje Automático.

No se trata de datos recolectados de forma manual, sino de registros administrativos oficiales publicados en formato abierto. Para este trabajo se realizó un proceso de selección y preprocesamiento con el objetivo de adaptar el dataset al problema de predicción planteado.

### Descripción general del dataset original

En la revisión inicial, el dataset completo presenta:

* Cantidad de instancias: 7.494 filas.
* Cantidad de columnas: 6 columnas.
* Formato del archivo: CSV.
* Unidad de análisis: registros mensuales de producción de gas por provincia y tipo de producción.
* Período observado: desde enero de 2009 hasta abril de 2026.

Cada fila representa un registro de producción para una provincia, un mes determinado y un tipo de producción de gas.

### Columnas del dataset original

| Columna         | Tipo de dato aproximado | Descripción                                                                              |
| --------------- | ----------------------- | ---------------------------------------------------------------------------------------- |
| `anio`          | Entero                  | Año correspondiente al registro de producción.                                           |
| `mes`           | Entero                  | Mes correspondiente al registro de producción.                                           |
| `indice_tiempo` | Fecha / texto           | Identificador temporal del registro, compuesto por año y mes.                            |
| `provincia`     | Texto                   | Provincia a la que corresponde el dato de producción.                                    |
| `concepto`      | Texto                   | Tipo de producción registrada. Puede ser producción convencional, shale gas o tight gas. |
| `cantidad_mm3`  | Decimal                 | Cantidad de gas producida, medida en millones de metros cúbicos.                         |

### Recorte utilizado para el proyecto

Para adaptar el dataset al problema de Aprendizaje Automático, se realizó un recorte del conjunto original.

Primero se seleccionaron las provincias patagónicas productoras incluidas en el análisis:

* Chubut.
* Neuquén.
* Río Negro.
* Santa Cruz.
* Tierra del Fuego.

Luego se seleccionaron únicamente los registros correspondientes al concepto:

**Producción convencional**

Con este recorte, el dataset queda compuesto por:

* 1.040 filas.
* 6 columnas originales.

Este resultado surge de considerar 5 provincias patagónicas durante 208 meses registrados.

### Dataset procesado

Luego del filtrado inicial, se realizó un proceso de preparación de datos para generar variables útiles para el modelo.

Las principales transformaciones realizadas fueron:

* Conversión de la variable temporal `indice_tiempo` a formato de fecha.
* Ordenamiento de los datos por provincia y período.
* Selección de registros correspondientes a producción convencional.
* Filtrado de provincias patagónicas.
* Revisión de valores faltantes.
* Creación de variables históricas de producción.
* Creación de variables temporales para representar el comportamiento mensual.
* Eliminación de registros iniciales sin datos históricos suficientes para calcular variables de rezago.

Después de este procesamiento, el dataset final utilizado para modelar queda compuesto por:

* 1.025 filas.
* 10 columnas.

La reducción de filas se debe a la creación de variables basadas en meses anteriores. Al calcular variables como la producción del mes anterior, la producción de dos meses antes y el promedio de los últimos tres meses, los primeros registros de cada provincia quedan sin información histórica suficiente y deben ser eliminados.

### Columnas del dataset procesado

| Columna                      | Tipo de dato aproximado | Descripción                                                              |
| ---------------------------- | ----------------------- | ------------------------------------------------------------------------ |
| `anio`                       | Entero                  | Año del registro.                                                        |
| `mes`                        | Entero                  | Mes del registro.                                                        |
| `indice_tiempo`              | Fecha / texto           | Identificador temporal del registro.                                     |
| `provincia`                  | Texto / categórica      | Provincia patagónica correspondiente al registro.                        |
| `concepto`                   | Texto / categórica      | Tipo de producción. En este proyecto se utiliza producción convencional. |
| `cantidad_mm3`               | Decimal                 | Producción mensual de gas. Es la variable objetivo.                      |
| `produccion_mes_anterior`    | Decimal                 | Producción registrada en el mes anterior para la misma provincia.        |
| `produccion_dos_meses_antes` | Decimal                 | Producción registrada dos meses antes para la misma provincia.           |
| `promedio_3_meses`           | Decimal                 | Promedio de producción de los tres meses anteriores.                     |
| `variacion_mes_anterior`     | Decimal                 | Variación de producción entre meses anteriores.                          |

### Información relevante del dataset

El dataset permite analizar la evolución mensual de la producción convencional de gas en provincias patagónicas. Esto es importante porque la Patagonia tiene un peso relevante dentro de la producción energética del país.

En el caso de Tierra del Fuego, el gas convencional tiene especial importancia por su relación con la Cuenca Austral, la producción offshore, las regalías provinciales, el empleo y la infraestructura energética.

Sin embargo, el dataset no incluye todos los factores que pueden afectar la producción, como inversiones, precios, mantenimiento de instalaciones, decisiones empresariales, entrada de nuevos pozos o cambios regulatorios. Por ese motivo, el modelo no buscará explicar completamente el comportamiento del sector gasífero, sino estimar la producción mensual a partir de datos históricos disponibles.

### Preprocesamiento realizado

El preprocesamiento realizado sobre los datos incluyó los siguientes pasos:

* Carga del archivo CSV original.
* Revisión de la cantidad de filas y columnas.
* Identificación de las variables disponibles.
* Filtrado de las provincias patagónicas.
* Selección del concepto producción convencional.
* Ordenamiento de los registros por provincia y fecha.
* Conversión de la columna temporal a formato de fecha.
* Creación de variables predictoras basadas en meses anteriores.
* Revisión de valores faltantes generados por las variables históricas.
* Eliminación de registros sin información suficiente para el entrenamiento.
* Preparación del dataset final para aplicar modelos de regresión.

### Tipo de problema asociado al dataset

El trabajo se plantea como un problema de regresión supervisada, porque la variable objetivo es numérica.

El modelo buscará estimar la producción mensual de gas convencional, medida en millones de metros cúbicos. No se trata de un problema de clasificación, ya que no se busca asignar categorías, sino predecir un valor continuo.

### Conclusión de la entrega

En esta segunda entrega se logró identificar, descargar y describir el dataset que será utilizado en el proyecto de Aprendizaje Automático.

El conjunto de datos seleccionado proviene de una fuente pública y oficial, cuenta con información histórica suficiente y permite construir un problema de regresión supervisada vinculado con la producción mensual de gas convencional en Tierra del Fuego y provincias patagónicas.

A partir del dataset original se realizó un recorte y un preprocesamiento inicial para obtener un conjunto de datos adecuado para la etapa posterior de modelado.

# Entrega 3: Modelo de Aprendizaje Automático y resultados

## Modelo y resultados

### 1. Recordatorio del origen de los datos

El proyecto utiliza el dataset **Producción gas SESCO más Tight y Shale capítulo IV por provincia**, publicado en el portal **Datos Argentina** y proveniente de registros oficiales de la **Secretaría de Energía de la Nación**.

El archivo se encuentra en formato CSV y contiene información mensual sobre producción de gas por provincia, tipo de producción y período de tiempo.

El dataset original contiene:

- **7.494 registros**.
- **6 columnas**.
- Período observado: **enero de 2009 a abril de 2026**.
- Unidad de análisis: producción mensual de gas por provincia y tipo de producción.

Las columnas principales del dataset original son:

| Columna | Descripción |
|---|---|
| `anio` | Año correspondiente al registro. |
| `mes` | Mes correspondiente al registro. |
| `indice_tiempo` | Identificador temporal del registro. |
| `provincia` | Provincia correspondiente al dato. |
| `concepto` | Tipo de producción registrada. |
| `cantidad_mm3` | Cantidad de gas producida, medida en millones de metros cúbicos. |

La variable `cantidad_mm3` representa la producción mensual de gas medida en millones de metros cúbicos.

---

### 2. Recorte utilizado

Para adaptar el dataset al problema de Aprendizaje Automático, se seleccionaron únicamente los registros correspondientes al concepto:

**Producción convencional**

Además, se trabajó con provincias patagónicas productoras de gas convencional:

- Tierra del Fuego.
- Santa Cruz.
- Chubut.
- Río Negro.
- Neuquén.

El objetivo inicial del proyecto estaba enfocado en Tierra del Fuego. Sin embargo, se decidió ampliar el análisis a otras provincias patagónicas para contar con una mayor cantidad de registros, mejorar la base de entrenamiento y permitir una comparación regional.

Después del filtrado, el dataset recortado quedó compuesto por:

- **1.040 registros**.
- **6 columnas**.

---

### 3. Análisis Exploratorio de Datos

Se realizó un Análisis Exploratorio de Datos para conocer la estructura del dataset, revisar las variables disponibles, identificar valores faltantes, observar la distribución de registros y analizar el comportamiento de la producción mensual de gas convencional.

El EDA incluyó:

- Revisión del tamaño del dataset.
- Revisión de columnas disponibles.
- Revisión de valores faltantes.
- Estadísticas descriptivas de la variable `cantidad_mm3`.
- Conteo de registros por provincia.
- Estadísticas descriptivas agrupadas por provincia.
- Gráfico de producción promedio mensual por provincia.
- Gráfico de evolución mensual de la producción convencional.
- Gráfico de distribución de la producción mensual por provincia.

---

### 4. Estadísticas relevantes

A partir del dataset original se identificaron **7.494 registros y 6 columnas**. Luego del recorte aplicado a producción convencional y provincias patagónicas, el dataset quedó con **1.040 registros**.

La variable más importante para el proyecto es `cantidad_mm3`, ya que representa la producción mensual de gas convencional y será la variable objetivo del modelo.

También se analizaron las diferencias por provincia. Este punto es importante porque la producción mensual no tiene el mismo comportamiento en todos los territorios. Neuquén aparece como una de las provincias con mayores niveles de producción promedio dentro del recorte analizado, mientras que Tierra del Fuego presenta niveles menores y una evolución más acotada.

---

### 5. Conclusiones del Análisis exploratorio de datos

El análisis exploratorio permitió observar que existen diferencias importantes entre las provincias seleccionadas.

En primer lugar, Neuquén presenta los mayores niveles de producción promedio mensual de gas convencional dentro del recorte trabajado. También se observa una tendencia descendente de la producción convencional entre los primeros años del período y los años más recientes.

Tierra del Fuego, que fue el foco inicial del proyecto, muestra niveles de producción menores en comparación con Neuquén. Su evolución se mantiene dentro de un rango más acotado, aunque con variaciones a lo largo del tiempo.

El EDA permite concluir que la variable `provincia` es relevante para el modelo, ya que la producción mensual no se comporta igual en todos los territorios. También se observa cierta continuidad temporal en las series de producción, por lo que resulta razonable construir variables históricas, como la producción del mes anterior, la producción de dos meses antes y el promedio de los tres meses previos.

---

### 6. Preparación del dataset para el modelo

Luego del análisis exploratorio, se preparó el dataset para aplicar modelos de Aprendizaje Automático.

Las principales transformaciones realizadas fueron:

- Conversión de la variable temporal a formato de fecha.
- Ordenamiento de los registros por provincia y fecha.
- Creación de variables históricas de producción.
- Eliminación de registros sin información histórica suficiente.
- Separación de variables predictoras y variable objetivo.
- Codificación de la variable categórica `provincia` mediante One Hot Encoding.
- Separación temporal entre datos de entrenamiento y prueba.

Las variables históricas creadas fueron:

| Variable | Descripción |
|---|---|
| `produccion_mes_anterior` | Producción registrada en el mes anterior para la misma provincia. |
| `produccion_dos_meses_antes` | Producción registrada dos meses antes para la misma provincia. |
| `promedio_3_meses` | Promedio de producción de los tres meses anteriores. |
| `variacion_mes_anterior` | Variación entre la producción del mes anterior y la producción de dos meses antes. |

Después de este procesamiento, el dataset final utilizado para modelar quedó compuesto por:

- **1.025 registros**.
- **10 columnas**.

La reducción de registros se debe a que, al crear variables históricas, los primeros meses de cada provincia no cuentan con datos anteriores suficientes y deben eliminarse.

---

### 7. Variable objetivo y variables predictoras

La variable objetivo del modelo es:

`cantidad_mm3`

Esta variable representa la producción mensual de gas convencional medida en millones de metros cúbicos.

Las variables predictoras utilizadas fueron:

- `anio`
- `mes`
- `provincia`
- `produccion_mes_anterior`
- `produccion_dos_meses_antes`
- `promedio_3_meses`
- `variacion_mes_anterior`

La variable `provincia` fue transformada mediante One Hot Encoding porque es una variable categórica de texto y los modelos de scikit-learn necesitan trabajar con valores numéricos.

---

### 8. Separación entre entrenamiento y prueba

Como el dataset contiene información mensual, se realizó una separación temporal entre entrenamiento y prueba. Esto permite respetar el orden cronológico de los datos y evitar que el modelo entrene con información futura.

Se utilizó aproximadamente:

- **80% de los datos iniciales para entrenamiento**.
- **20% de los datos finales para prueba**.

La fecha de corte fue **diciembre de 2022**.

El conjunto de entrenamiento quedó compuesto por:

- **820 registros**.

El conjunto de prueba quedó compuesto por:

- **205 registros**.

---

### 9. Modelos de Aprendizaje Automático utilizados

El problema se planteó como una tarea de regresión supervisada, porque el objetivo es estimar un valor numérico continuo: la producción mensual de gas convencional.

Se entrenaron dos modelos:

#### Regresión lineal

La regresión lineal fue utilizada como modelo principal. Este algoritmo permite estimar una variable numérica a partir de una combinación de variables predictoras.

En este caso, el modelo intenta encontrar una relación entre la producción mensual y variables como el año, el mes, la provincia y la producción registrada en meses anteriores.

La regresión lineal no utiliza hiperparámetros principales en esta implementación, por lo que fue tomada como modelo base.

#### Árbol de decisión para regresión

También se entrenó un árbol de decisión para regresión como modelo de comparación.

Este modelo permite construir reglas de decisión a partir de las variables predictoras y puede captar relaciones que no necesariamente sean lineales.

Para evitar que el árbol creciera demasiado y se ajustara excesivamente a los datos de entrenamiento, se utilizó el hiperparámetro:

`max_depth = 5`

También se utilizó:

`random_state = 42`

Esto permite que el resultado sea reproducible.

---

### 10. Métricas de evaluación

Para evaluar los modelos se utilizaron métricas de regresión.

La consigna menciona métricas como precisión, recall y F1-score, pero esas métricas se utilizan principalmente en problemas de clasificación. En este proyecto no se predice una categoría, sino un valor numérico. Por ese motivo, se utilizaron métricas adecuadas para regresión.

Las métricas utilizadas fueron:

#### MAE

El MAE, o error absoluto medio, mide cuánto se equivoca el modelo en promedio. Se expresa en la misma unidad que la variable objetivo.

#### RMSE

El RMSE, o raíz del error cuadrático medio, también mide el error, pero penaliza más los errores grandes.

#### R2

El R2, o coeficiente de determinación, indica qué parte de la variación de los datos logra explicar el modelo.

---

### 11. Resultados obtenidos

Los resultados obtenidos fueron los siguientes:

| Modelo | MAE | RMSE | R2 |
|---|---:|---:|---:|
| Regresión lineal | 15.675 | 54.951 | 0,78 |
| Árbol de decisión | 24.507 | 59.600 | 0,74 |

A partir de estos resultados, la regresión lineal obtuvo mejor desempeño que el árbol de decisión, ya que presentó:

- Menor MAE.
- Menor RMSE.
- Mayor R2.

Por ese motivo, la regresión lineal fue seleccionada como el modelo principal del proyecto.

---

### 12. Interpretación de los resultados

La regresión lineal logró aproximarse razonablemente a los valores reales de producción mensual de gas convencional. El valor de R2 de 0,78 indica que el modelo logra explicar una parte importante de la variación observada en los datos, aunque no la totalidad.

El árbol de decisión también logró captar parte del comportamiento de la producción, pero tuvo errores mayores. Su MAE y RMSE fueron más altos que los de la regresión lineal, y su R2 fue menor.

El gráfico de producción real versus producción predicha permite observar que el modelo sigue parte de la tendencia general de los datos, aunque no reproduce perfectamente todos los valores. Esto es esperable, ya que el modelo utiliza variables históricas simples y no incorpora factores externos que también pueden afectar la producción.

En el caso de Tierra del Fuego, el gráfico específico permite observar cómo se comporta el modelo sobre la provincia que motivó inicialmente el proyecto. La comparación muestra que el modelo puede funcionar como una primera aproximación, aunque todavía presenta limitaciones.

---

### 13. Limitaciones del modelo

El modelo desarrollado presenta algunas limitaciones importantes.

En primer lugar, utiliza una cantidad reducida de variables predictoras. Se trabaja principalmente con variables temporales, provinciales y valores históricos de producción.

El dataset no incluye otros factores que pueden influir en la producción de gas, como:

- Nuevos pozos.
- Inversiones.
- Mantenimiento de instalaciones.
- Infraestructura disponible.
- Empresas operadoras.
- Precios de la energía.
- Cambios regulatorios.
- Decisiones empresariales.
- Condiciones técnicas de los yacimientos.

Además, el dataset está agregado por provincia y mes. Esto significa que no se trabaja con información más detallada por yacimiento, pozo, área de producción u operador.

Por estas razones, el modelo no debe interpretarse como una herramienta definitiva de predicción energética, sino como una primera aproximación académica al problema.

---

### 14. Conclusiones finales

El proyecto permitió aplicar un flujo básico de Aprendizaje Automático supervisado sobre un dataset real, público y oficial.

A partir del problema formulado en la primera entrega, se logró construir un modelo de regresión para estimar la producción mensual de gas convencional en Tierra del Fuego y provincias patagónicas.

El trabajo incluyó la selección del dataset, el preprocesamiento de los datos, el análisis exploratorio, la construcción de variables históricas, la separación entre entrenamiento y prueba, el entrenamiento de modelos y la evaluación de resultados.

La regresión lineal fue el modelo con mejor desempeño dentro de los modelos probados. Obtuvo menor error y mejor nivel de ajuste que el árbol de decisión.

La conclusión principal es que la producción mensual de gas convencional puede estimarse parcialmente a partir de datos históricos y variables temporales. Sin embargo, para mejorar el modelo sería necesario incorporar más variables explicativas y trabajar con información más detallada del sector hidrocarburífero.

---

### 15. Archivos incluidos en el repositorio

La entrega debe quedar respaldada en el repositorio Git, incluyendo:

- Dataset original en la carpeta `data/raw`.
- Dataset procesado en la carpeta `data/processed`.
- Notebook principal con EDA, modelos y resultados en la carpeta `notebooks`.
- Documentos del proyecto en la carpeta `reports`.
- Modelos entrenados guardados en la carpeta `models`.
- Video de presentación en la carpeta `video` o link indicado en el README.
- Archivo `requirements.txt` con las librerías utilizadas.
- Archivo `README.md` con la descripción general del proyecto.

