"Estimación de la producción mensual de gas convencional en Tierra del Fuego y provincias patagónicas"

(corresponde a la entrega 1)

## Descripción del proyecto

Este proyecto propone aplicar modelos de aprendizaje automático supervisado para estimar la producción mensual de gas convencional en Tierra del Fuego, Antártida e Islas del Atlántico Sur.

La idea central es trabajar con datos históricos oficiales de producción hidrocarburífera y analizar si algunas variables temporales, junto con valores de producción de meses anteriores, pueden servir para aproximar la producción de un mes determinado.

El trabajo se enfoca en la producción convencional de gas, ya que en el caso de Tierra del Fuego los registros de shale gas y tight gas aparecen con valores en cero dentro del dataset seleccionado.

## Contexto del problema

Tierra del Fuego tiene una relación histórica con la producción de hidrocarburos. Dentro de esa actividad, el gas natural ocupa un lugar importante por la presencia de la Cuenca Austral y por el desarrollo de áreas de producción ubicadas tanto en tierra como en zonas offshore.

La producción de gas forma parte de una cadena productiva más amplia. Primero se encuentra la etapa de exploración y producción, donde las empresas operadoras trabajan sobre áreas o concesiones para extraer el recurso. Luego aparece el tratamiento del gas en plantas ubicadas principalmente en la zona norte de la isla y finalmente su transporte hacia el sistema nacional, mediante infraestructura conectada al Gasoducto San Martín.

En Tierra del Fuego conviven operaciones onshore y offshore. Las primeras se desarrollan en tierra, mientras que las segundas se realizan costa afuera. Esta característica hace que la producción gasífera fueguina tenga una dimensión técnica, logística y económica importante.

Entre los actores privados con presencia en la producción fueguina aparecen empresas vinculadas a desarrollos de la Cuenca Marina Austral, como TotalEnergies, Harbour Energy y Pan American Energy. En los últimos años, el proyecto Fénix volvió a poner en agenda la producción offshore de gas natural frente a Tierra del Fuego.

Para la provincia, la producción de gas tiene relevancia porque se vincula con regalías, empleo directo e indirecto, contratación de servicios, actividad portuaria, infraestructura energética y planificación económica. Para el país, también tiene importancia porque aporta al abastecimiento de gas natural dentro de la matriz energética argentina.

Desde el punto de vista del aprendizaje automático, la producción mensual de gas convencional puede analizarse como una variable numérica observada a lo largo del tiempo. Esto permite formular un problema de regresión, ya que el objetivo no es clasificar casos, sino estimar un valor de producción.

## Problema que se abordará

El problema que se abordará es la estimación de la producción mensual de gas convencional en Tierra del Fuego a partir del comportamiento histórico de la propia serie de producción.

La pregunta orientadora del proyecto es, ¿Es posible estimar la producción mensual de gas convencional en Tierra del Fuego utilizando variables temporales y valores históricos de producción?

## Relevancia del problema

El problema es relevante porque permite aplicar aprendizaje automático a un tema vinculado con la producción energética de Tierra del Fuego.

Además, permite trabajar con una fuente oficial de datos. Esto evita construir una variable objetivo sintética o artificial. La producción mensual de gas convencional es un dato registrado, medible y comparable en el tiempo.

El proyecto también permite analizar las posibilidades y limitaciones de los modelos de aprendizaje automático cuando se trabaja con datos reales. Si bien el dataset permite observar la producción mensual, no incluye todos los factores que pueden afectar esa producción, como precios, inversiones, decisiones empresariales, mantenimiento de instalaciones, entrada de nuevos pozos o cambios regulatorios.

Por eso, el trabajo se enfocará en estimar la producción a partir de datos históricos, reconociendo esas limitaciones.

## Dataset seleccionado

La fuente utilizada será el dataset **Producción gas SESCO más Tight y Shale capítulo IV por provincia**, publicado en el portal Datos Argentina.

El archivo se encuentra en formato CSV y contiene información oficial sobre producción de gas.

Las columnas principales del dataset son:

- `anio`
- `mes`
- `indice_tiempo`
- `provincia`
- `concepto`
- `cantidad_mm3`

Para este proyecto se utilizarán los registros correspondientes a Tierra del Fuego y al concepto **Producción convencional**.

La variable `cantidad_mm3` representa la producción mensual de gas medida en millones de metros cúbicos.

## Tipo de problema

El proyecto se plantea como un problema de **regresión**, porque la variable objetivo es numérica.

El valor que se buscará estimar será la producción mensual de gas convencional en Tierra del Fuego.

No se trata de un problema de clasificación, ya que el objetivo no es asignar categorías, sino predecir un valor continuo de producción.

## Variable objetivo

La variable objetivo será:

- `cantidad_mm3`

Esta columna representa la producción mensual de gas convencional medida en millones de metros cúbicos.

El modelo intentará estimar esta variable a partir de información temporal y de valores históricos de producción.

## Variables predictoras posibles

Las variables predictoras iniciales estarán relacionadas con el comportamiento temporal de la producción.

Entre ellas se podrán utilizar:

- Año
- Mes
- Número de período
- Producción del mes anterior
- Producción de dos meses anteriores
- Promedio de producción de los últimos tres meses
- Variación respecto del mes anterior

Estas variables podrán ajustarse durante la etapa de preprocesamiento, según la calidad de los datos y los resultados del análisis exploratorio.

## Tratamiento inicial de los datos

Para preparar el dataset se prevén los siguientes pasos:

- Filtrar los registros correspondientes a Tierra del Fuego.
- Seleccionar únicamente el concepto **Producción convencional**.
- Ordenar los datos por año y mes.
- Revisar valores faltantes o atípicos.
- Crear variables temporales simples.
- Crear variables históricas a partir de meses anteriores.
- Separar datos de entrenamiento y prueba.
- Evaluar el comportamiento de la serie mensual de producción.

Un punto a revisar será el registro de abril de 2026, porque aparece con un valor muy inferior al de los meses previos. En el análisis exploratorio se deberá observar si se trata de un dato parcial, atípico o incompleto.

## Modelos posibles

Se trabajará con modelos supervisados de regresión vistos o relacionados con los contenidos de la materia.

### Regresión lineal

Será el modelo base. Servirá para observar si las variables predictoras permiten aproximar la producción mensual de gas convencional.

### K vecinos más cercanos para regresión

Este modelo permitirá estimar valores a partir de meses con características similares. Se relaciona con el contenido de KNN trabajado en la materia.

### Árbol de decisión para regresión

Este modelo permitirá construir reglas de decisión y captar relaciones que no necesariamente sean lineales.

### Random Forest Regressor

De manera opcional, se podrá incorporar un modelo de ensamble como comparación adicional. No será el modelo principal, sino una referencia para observar si mejora los resultados respecto de modelos más simples.

## Métricas de evaluación previstas

Al tratarse de un problema de regresión, se utilizarán métricas adecuadas para evaluar errores en valores numéricos.

### MAE

El error absoluto medio permite conocer el error promedio de predicción en la misma unidad de la producción.

### RMSE

La raíz del error cuadrático medio penaliza más los errores grandes, por lo que permite observar si el modelo comete errores importantes en algunos meses.

### R2

El coeficiente de determinación permite observar qué parte de la variación de la producción logra explicar el modelo.

## Objetivo general

Aplicar modelos de aprendizaje automático supervisado para estimar la producción mensual de gas convencional en Tierra del Fuego a partir de datos históricos oficiales.

## Objetivos específicos

- Describir el contexto productivo del gas natural en Tierra del Fuego.
- Identificar una fuente oficial de datos sobre producción de gas.
- Filtrar y preparar los registros correspondientes a Tierra del Fuego.
- Explorar la evolución mensual de la producción mediante gráficos y medidas descriptivas.
- Preparar el dataset mediante limpieza, selección de variables y creación de variables temporales.
- Entrenar modelos de regresión utilizando Python y scikit-learn.
- Evaluar los modelos mediante métricas como MAE, RMSE y R2.
- Comparar los resultados obtenidos entre los modelos utilizados.
- Elaborar conclusiones sobre el desempeño de los modelos y sus limitaciones.

## Resultados esperados

Se espera que los modelos puedan captar parte del comportamiento histórico de la producción mensual de gas convencional, especialmente a partir de la producción de meses anteriores y de variables temporales como mes y año.

