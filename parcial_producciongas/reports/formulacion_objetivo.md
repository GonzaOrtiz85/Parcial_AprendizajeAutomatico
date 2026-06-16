Título 
“Estimación de la producción mensual de gas convencional en Tierra del Fuego mediante modelos de regresión supervisada”

____________________________________
Tema del proyecto

Este proyecto propone aplicar modelos de aprendizaje automático supervisado para estimar la producción mensual de gas convencional en Tierra del Fuego, Antártida e Islas del Atlántico Sur.
La idea es trabajar con datos históricos oficiales de producción hidrocarburífera y analizar si algunas variables temporales, junto con valores de producción de meses anteriores, pueden servir para aproximar la producción de un mes determinado.

Proceso de selección del tema

Antes de llegar a esta propuesta se analizaron otras alternativas. Entre ellas se propusieron temas relacionados con comportamiento electoral, proyectos con dataset de calefacción y gas con datos asociados a sensores.
Esas opciones fueron descartadas por recomendación del docente. En algunos casos, los proyectos carecían de originalidad. En otros, no existían datos locales fiables que permitieran desarrollar el trabajo.
A partir de la recomendación del docente de buscar alternativas más originales y con valor local, se decidió avanzar con un tema productivo y energético. La producción de gas convencional en Tierra del Fuego permite trabajar con datos oficiales, una variable objetivo real y un problema vinculado con la estructura económica de la provincia.
Contexto del problema
Tierra del Fuego tiene una relación histórica con la producción de hidrocarburos. Dentro de esa actividad, el gas natural ocupa un lugar importante por la presencia de la Cuenca Austral y por el desarrollo de áreas de producción ubicadas tanto en tierra como en zonas offshore.
El negocio del gas en la provincia forma parte de una cadena productiva más amplia. Primero está la etapa de exploración y producción, donde las empresas operadoras trabajan sobre áreas o concesiones para extraer el recurso. Después aparece el tratamiento del gas en plantas ubicadas en la zona norte de la isla y finalmente su transporte hacia el sistema nacional, principalmente a través de infraestructura conectada con el Gasoducto San Martín.
En Tierra del Fuego conviven operaciones onshore y offshore. Las primeras se desarrollan en tierra, mientras que las segundas se realizan costa afuera, sobre plataformas ubicadas en el mar. Esta característica hace que la producción gasífera fueguina tenga una dimensión técnica y logística importante, ya que no depende solo del recurso natural, sino también de inversiones, pozos, plantas de tratamiento, ductos, mantenimiento e infraestructura de transporte.
Entre los actores privados con presencia en la producción fueguina aparecen empresas como TotalEnergies, Harbour Energy y Pan American Energy, asociadas a desarrollos de la Cuenca Marina Austral. En los últimos años, el proyecto Fénix volvió a poner en agenda la producción offshore de gas natural frente a Tierra del Fuego. Este tipo de proyectos muestra que la actividad no debe mirarse únicamente como una serie de datos históricos, sino como parte de un sector económico con empresas, inversiones, tecnología e impacto fiscal.
Para la provincia, la producción de gas tiene relevancia porque se vincula con regalías, empleo directo e indirecto, contratación de servicios, actividad portuaria, infraestructura energética y planificación económica. Para el país, también tiene importancia porque aporta al abastecimiento de gas natural dentro de la matriz energética argentina.
Desde el punto de vista del aprendizaje automático, la producción mensual de gas convencional puede trabajarse como una variable numérica observada a lo largo del tiempo. Esto permite formular un problema de regresión, ya que el objetivo no es clasificar casos, sino estimar un valor de producción.
De todos modos, el modelo no pretende explicar por completo el negocio gasífero. El dataset permite observar producción mensual, pero no incluye todos los factores que pueden afectar esa producción, como precios, inversiones, decisiones empresariales, mantenimiento de instalaciones, entrada de nuevos pozos o cambios regulatorios. Por eso, el trabajo se enfocará en estimar la producción a partir de datos históricos, reconociendo esas limitaciones.

Problema que se abordará

El problema que se abordará es la estimación de la producción mensual de gas convencional en Tierra del Fuego a partir del comportamiento histórico de la propia serie de producción.
La pregunta orientadora del proyecto será la siguiente. ¿Es posible estimar la producción mensual de gas convencional en Tierra del Fuego utilizando variables temporales y valores históricos de producción?

Relevancia del problema

El problema es relevante porque permite aplicar aprendizaje automático a un tema vinculado con la producción energética de Tierra del Fuego.
También permite trabajar con una fuente oficial de datos. Esto evita construir una variable objetivo sintética o artificial. La producción mensual de gas convencional es un dato registrado, medible y comparable en el tiempo.

Dataset seleccionado

La fuente será el dataset Producción gas SESCO más Tight y Shale capítulo IV por provincia, publicado en el portal Datos Argentina.
El archivo está en formato CSV y contiene información oficial sobre producción de gas. En la revisión inicial se observó que tiene 7494 filas y 6 columnas.
Las columnas del archivo son las siguientes.
anio
mes
indice_tiempo
provincia
concepto
cantidad_mm3
Para este proyecto se utilizarán los registros correspondientes a Tierra del Fuego. En ese recorte, el dataset contiene 624 filas. Esas filas corresponden a 208 meses registrados y a tres conceptos de producción por cada mes.
Los conceptos que aparecen para Tierra del Fuego son los siguientes.
Producción convencional
Shale gas
Tight gas
En el caso fueguino, Shale gas y Tight gas aparecen con valores en cero. Por eso, el trabajo se concentrará en la producción convencional de gas.
Tipo de problema
El proyecto se plantea como un problema de regresión supervisada, porque la variable objetivo es numérica. El valor que se buscará estimar será la producción mensual de gas convencional en Tierra del Fuego.
Variable objetivo
La variable objetivo será cantidad_mm3. Esta columna representa la producción mensual de gas convencional medida en millones de metros cúbicos.
El modelo intentará estimar esa variable a partir de información temporal y de valores históricos de producción.

Variables predictoras posibles

Las variables predictoras iniciales estarán relacionadas con el comportamiento temporal de la producción.
-Año
-Mes
-Número de período
-Producción del mes anterior
-Producción de dos meses anteriores
-Promedio de producción de los últimos tres meses
-Variación respecto del mes anterior

Estas variables podrán ajustarse durante la etapa de preprocesamiento. 

Tratamiento inicial de los datos

Para preparar el dataset se prevén los siguientes pasos.
-Filtrar los registros correspondientes a Tierra del Fuego.
-Seleccionar únicamente el concepto Producción convencional.
-Ordenar los datos por año y mes.
-Revisar valores faltantes o atípicos.
-Crear variables temporales simples.
-Crear variables históricas a partir de meses anteriores.
-Separar datos de entrenamiento y prueba.
-Un punto a revisar será el registro de abril de 2026, porque aparece con un valor muy inferior al de los meses previos. En el análisis exploratorio se deberá observar si se trata de un dato parcial, atípico o incompleto.

Modelos posibles

Se trabajará con modelos supervisados de regresión vistos o relacionados con los contenidos de la materia.
Regresión lineal: Será el modelo base. Servirá para observar si las variables predictoras permiten aproximar la producción mensual de gas convencional.
K vecinos más cercanos para regresión: Este modelo permitirá estimar valores a partir de meses con características similares. Se relaciona con el contenido de KNN trabajado en la materia.
Árbol de decisión para regresión: Este modelo permitirá construir reglas de decisión y captar relaciones que no necesariamente sean lineales.
Modelo adicional opcional: Si el desarrollo del trabajo lo permite, se podrá incorporar Random Forest Regressor como comparación adicional. No será el modelo principal, sino una referencia para observar si un modelo de ensamble mejora los resultados.

Métricas de evaluación previstas

Al tratarse de un problema de regresión, se utilizarán métricas adecuadas para evaluar errores en valores numéricos.
MAE: Error absoluto medio. Permite conocer el error promedio de predicción en la misma unidad de la producción.
RMSE: Raíz del error cuadrático medio. Penaliza más los errores grandes.
R2: Coeficiente de determinación. Permite observar qué parte de la variación de la producción logra explicar el modelo.

Objetivo general

Aplicar modelos de aprendizaje automático supervisado para estimar la producción mensual de gas convencional en Tierra del Fuego a partir de datos históricos oficiales.

Objetivos específicos

-Describir el contexto productivo del gas natural en Tierra del Fuego.
-Identificar una fuente oficial de datos sobre producción de gas.
-Filtrar y preparar los registros correspondientes a Tierra del Fuego.
-Explorar la evolución mensual de la producción mediante gráficos y medidas descriptivas.
-Preparar el dataset mediante limpieza, selección de variables y creación de variables temporales.
-Entrenar modelos de regresión utilizando Python y scikit-learn.
-Evaluar los modelos mediante métricas como MAE, RMSE y R2.
-Comparar los resultados obtenidos entre los modelos utilizados.
-Elaborar conclusiones

REsultados esperados

Se espera que los modelos puedan captar parte del comportamiento histórico de la producción mensual de gas convencional, especialmente a partir de la producción de meses anteriores y de variables temporales como mes y año.
También es posible que los modelos tengan limitaciones para anticipar cambios bruscos. La producción de hidrocarburos puede verse afectada por inversiones, mantenimiento, entrada de nuevos proyectos, decisiones empresariales o factores técnicos que no estén incluidos en el dataset.
Referencias
-Datos Argentina. Producción gas SESCO más Tight y Shale capítulo IV por provincia. Recurso en formato CSV incluido dentro del dataset Producción de Petróleo y Gas SESCO
-Secretaría de Energía de la Nación. Producción de Petróleo y Gas. 

