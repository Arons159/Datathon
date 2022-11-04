![HenryLogo](https://d31uz8lwfmyn8g.cloudfront.net/Assets/logo-henry-white-lg.png)
​
# Proyecto individual 2
​
En este segundo proyecto se puso en practica habilidades en el campo de la predicción. se uso la libreria <kbd>sklearn</kbd> de python para medir la performance del modelo, la cual a su vez, será usada para entrenar y predecir el modelo del dataset.
​
## Planteamiento del Problema
​
Dentro de la sociedad globalizada e industrializada, es sabido que los precios de los inmuebles han presentado un constante cambio, por lo que quienes deseen invertir o vender una propiedad se enfrentan al fenómeno especulativo existente en la valorización de éstos. Esto, debido a la constante tendencia de las ciudades a crecer demográfica y comercialmente, llegando a un punto en donde no se tiene certeza de la valorización real dentro del sector en donde se desee invertir. 
​
Pese a que el precio depende, en cierta medida, de las tendencias que esté teniendo el mercado inmobiliario en un determinado tiempo, poder estimar adecuadamente el valor de una propiedad es una referencia clave para entender si es una buena oportunidad, ya sea de compra o de venta.
​
## Descripción del problema
​
Usted ha sido contactado de una importante empresa inversora dentro del rubro de la inmobiliaria en Colombia, con el fin de que implemente un modelo de clasificación que permita clasificar el precio de las propiedades en venta, utilizando los datos que se han puesto a su disposición correspondientes al año 2020.
​
Para esto, específicamente, debe predecir la **categorización** de las propiedades entre baratas o caras, considerando como criterio el valor promedio de los precios (la media). 
​
## Desarrollo
​
Se utilizó un archivoJupyter Notebook: <kbd>Datathon.ipynb</kbd>, el cual incluye un proceso EDA, en donde se utilizo dos archivos llamados <kbd>properties_colombia_train</kbd>, utilizado para entrenar los datos y  <kbd>properties_colombia_test</kbd> 
para poder probar las predicciones de este modelo.

## Descripción de las dimensiones
- id - Identificador del aviso. No es único: si el aviso es actualizado por la inmobiliaria (nueva versión del aviso) se crea un nuevo registro con la misma id pero distintas fechas: de alta y de baja.
- ad_type - Tipo de aviso (Propiedad, Desarrollo/Proyecto).
- start_date - Fecha de alta del aviso.
- end_date - Fecha de baja del aviso.
- created_on - Fecha de alta de la primera versión del aviso.
- lat - Latitud.
- lon - Longitud.
- l1 - Nivel administrativo 1: país.
- l2 - Nivel administrativo 2: usualmente provincia.
- l3 - Nivel administrativo 3: usualmente ciudad.
- l4 - Nivel administrativo 4: usualmente barrio.
- l5 - Nivel administrativo 5.
- l6 - Nivel administrativo 6.
- rooms - Cantidad de ambientes.
- bedrooms - Cantidad de dormitorios (útil en el resto de los países).
- bathrooms - Cantidad de baños.
- surface_total - Superficie total en m².
- surface_covered - Superficie cubierta en m².
- price - Precio publicado en el anuncio.
- currency - Moneda del precio publicado.
- price_period - Periodo del precio (Diario, Semanal, Mensual)
- title - Título del anuncio.
- description - Descripción del anuncio.
- property_type - Tipo de propiedad (Casa, Departamento, PH).
- operation_type - Tipo de operación (Venta).
- geometry - Puntos geométricos formados por las coordenadas latitud y longitud. 

## Pasos a seguir

Primero se importan las liberias necesarias para leer los archivos y trabajar con estos
```
import numpy as np 
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```
- Luego se leen los archivos csv como dataframe
- Se inspeccionan las variables
- Cambiamos los nulos de las variables numericas por ceros 
- Creamos una nueva columna clasificatoria segun el precio promedio, de tal manera que nos queda entre caro o barato el inmueble
- Seleccionamos las columnas que nos interesan y no nos generan ruido
- aplicamos un cambio de las variables no numericas hacia una numerica

Pasos para la el modelado Machine Learning:

```
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import train_test_split
from sklearn import metrics
from sklearn.metrics import confusion_matrix
from sklearn.metrics import recall_score
```
- Entrenamos el dataframe test utilicando el <kbd>RandomForestClassifier</kbd>, el cual realiza arborles de decision aleatorios que nos ayudan a predecir el modelo.
- Entrenamos el modelo haciendo un split de la dataframe
- Posteriormente predecimos el test
- Se calcula el Accuracy y tambien se aplica la Matriz de Confusion para que gracias a este podamos calcular el recall y verificar la precision de nuestro modelo predictivo
- Finalmente se guardan las respuestas en un archivo csv para que pueda ser enviado como respuesta

​
## Métrica a utilizar

Como método de evaluación del desempeño del modelo, se utilizará la métrica de Exhaustividad (Recall) para las propiedades caras, a partir de la matriz de confusión (Confusion Matrix). 

​
$ Recall=\frac{TP}{TP+FN}$

​
Donde $TP$ son los verdaderos positivos y $FN$ los falsos negativos.

Adicionalmente, se incluye la Accuracy como métrica de control.
​

​ 
