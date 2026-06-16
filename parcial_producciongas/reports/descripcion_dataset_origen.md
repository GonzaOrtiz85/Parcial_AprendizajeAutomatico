Descripción del dataset y origen

Dataset seleccionado

Para el proyecto de Aprendizaje Automático se utilizará el dataset Producción de Petróleo y Gas SESCO, publicado por la Secretaría de Energía en el portal Datos Argentina.
Dentro de ese conjunto de datos, se trabajará con el recurso Producción gas SESCO más Tight y Shale capítulo IV por provincia, disponible en formato CSV.
El objetivo del proyecto es estimar la producción mensual de gas convencional en provincias patagónicas, manteniendo a Tierra del Fuego como caso principal de análisis.

En una primera formulación del proyecto se había previsto trabajar únicamente con los registros correspondientes a Tierra del Fuego. Sin embargo, durante la revisión del dataset se observó que ese recorte dejaba una cantidad limitada de registros para entrenar modelos de Aprendizaje Automático. Por ese motivo, se decidió reenfocar el trabajo hacia un recorte regional de provincias patagónicas productoras de gas convencional. 

Origen del dataset

El dataset proviene del portal Datos Argentina, que reúne datos abiertos publicados por organismos del Estado nacional.
La información corresponde a la Secretaría de Energía y forma parte de los registros oficiales de producción de hidrocarburos del sistema SESCO.
Fuente
Datos Argentina
Organismo responsable
Secretaría de Energía de la Nación
Dataset
Producción de Petróleo y Gas SESCO
Recurso utilizado
Producción gas SESCO más Tight y Shale capítulo IV por provincia
Formato
CSV
Fecha de adquisición
3 de junio de 2026

Descripción general del archivo original

El archivo original contiene 7494 instancias y 6 columnas.
La frecuencia de los datos es mensual.
El período registrado va desde enero de 2009 hasta abril de 2026.
Las columnas originales del dataset son las siguientes.
anio
mes
indice_tiempo
provincia
concepto
cantidad_mm3

Características del dataset

A continuación se describen las columnas principales del archivo.
anio
Indica el año correspondiente al registro.
mes
Indica el mes correspondiente al registro, con valores numéricos del 1 al 12.
indice_tiempo
Representa el período temporal del registro. Permite ordenar los datos de manera cronológica.
provincia
Indica la provincia o jurisdicción asociada al dato de producción.
concepto
Indica el tipo de producción registrada. En el archivo aparecen Producción convencional, Shale gas y Tight gas.
cantidad_mm3
Indica la cantidad de gas producida, medida en millones de metros cúbicos. Esta será la variable objetivo del proyecto.

Tipos de datos

En la revisión inicial realizada en Google Colab, el dataset fue cargado correctamente con pandas.
Las columnas anio y mes corresponden a variables numéricas enteras.
La columna cantidad_mm3 corresponde a una variable numérica.
Las columnas indice_tiempo, provincia y concepto corresponden a variables categóricas o de texto.

Recorte aplicado

Para preparar el dataset de acuerdo con el objetivo del proyecto, se aplicaron dos filtros principales.
Primero, se seleccionó únicamente el concepto Producción convencional.
Segundo, se seleccionaron provincias patagónicas productoras de gas.
Las provincias incluidas en el recorte son las siguientes.
Tierra del Fuego
Santa Cruz
Chubut
Rio Negro
Neuquén
Este recorte permite trabajar con una base más amplia que si se utilizara únicamente Tierra del Fuego, pero mantiene el interés territorial del proyecto. Tierra del Fuego seguirá siendo el caso principal de análisis.

Dataset luego del recorte

Después de filtrar el concepto Producción convencional y seleccionar las provincias patagónicas, el dataset quedó conformado por 1040 registros.
Luego se construyeron variables históricas por provincia y se eliminaron las filas que no tenían datos suficientes por el uso de rezagos.
El dataset final preparado para la etapa de Machine Learning quedó conformado por 1025 instancias y 10 columnas.
La distribución final por provincia quedó equilibrada.
Chubut, 205 registros
Neuquén, 205 registros
Rio Negro, 205 registros
Santa Cruz, 205 registros
Tierra del Fuego, 205 registros

Variables construidas durante el preprocesamiento

Para adaptar el dataset a un problema de Aprendizaje Automático, se construyeron variables predictoras a partir de la producción de meses anteriores.
Las variables construidas fueron las siguientes.
produccion_mes_anterior
produccion_dos_meses_antes
promedio_3_meses
variacion_mes_anterior
Estas variables fueron calculadas por provincia. Esto es importante porque la producción anterior de Tierra del Fuego debe calcularse usando la serie de Tierra del Fuego, y no valores de otra provincia.

Variable objetivo

La variable objetivo será cantidad_mm3.
Esta variable representa la producción mensual de gas convencional medida en millones de metros cúbicos.
Como se trata de una variable numérica continua, el proyecto corresponde a un problema de regresión.

Columnas del dataset final

Luego del preprocesamiento inicial, el dataset final quedó compuesto por las siguientes columnas.
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

Proceso de recopilación y preprocesamiento realizado

El proceso realizado hasta esta entrega fue el siguiente.
Se descargó el archivo CSV desde el portal Datos Argentina.
Se cargó el archivo en Google Colab utilizando pandas.
Se revisaron las dimensiones del archivo original.
Se revisaron los nombres de columnas.
Se identificaron los conceptos disponibles en la columna concepto.
Se filtró el concepto Producción convencional.
Se seleccionaron las provincias patagónicas productoras.
Se ordenaron los datos por provincia, año y mes.
Se construyeron variables históricas por provincia.
Se eliminaron las filas sin datos suficientes generadas por los rezagos.
Se generó un dataset final preparado para la etapa de modelado.

Archivos incluidos en el repositorio Git

Para esta entrega, el repositorio Git incluirá los siguientes archivos y carpetas.
data/raw
Contiene el archivo CSV original descargado desde Datos Argentina.
data/processed
Contiene el archivo procesado con el recorte patagónico y las variables históricas construidas.
notebooks
Contiene la notebook de Google Colab utilizada para cargar, revisar y preparar el dataset.
reports
Contiene el documento correspondiente a esta entrega.

Conclusión de la entrega

El dataset seleccionado es adecuado para continuar con el proyecto porque tiene origen oficial, formato CSV, frecuencia mensual, una variable objetivo numérica y datos suficientes para construir variables predictoras.
El recorte aplicado permite trabajar con provincias patagónicas productoras de gas convencional, manteniendo a Tierra del Fuego como caso principal de análisis. Además, el preprocesamiento realizado transforma el archivo original en una base más adecuada para entrenar modelos de regresión en la siguiente etapa del proyecto.
Referencias
Datos Argentina. Producción de Petróleo y Gas SESCO. Secretaría de Energía de la Nación.
Datos Argentina. Producción gas SESCO más Tight y Shale capítulo IV por provincia.
Programa de la materia Aprendizaje Automático 2026.
