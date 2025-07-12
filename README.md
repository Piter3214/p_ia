**Definicion del problema.**

El fraude con las tarjetas de credito es un problema grave que afecta a muchas personas y organizaciones financieras como banco y empresa de tarjetas,comercios y consumidores. este tipo de fraude genera perdidas economicas significativas.


Ademas este tipo de fraudes generan un costo operativo asociado a la deteccion de estos mismos ya que al revisar altos volumenes de datos (transacciones) a tiempo real, una mala deteccion conlleva a tener errores relevantes:
        
Falsos negativos: Transacciones fraudulentas que no son detectadas.

Falsos positivos: Transacciones legítimas que son detectadas como fraudulentas

Estos errores provocan la desconfianza de los clientes hacia el sistema financiera de las tarjetas de credito, conllevando a una posible perdida de clientes y a su vez generando mala reputacion de las entidades involucradas.


**Plan de accion:**

Descripcion  del dataset:

El data set abarca los fraudes de las transacciones de las tajetas de creditos el cual la moneda del dataset esta en libras, cuenta con 16 columnas las cuales son las siguientes:

                ID de transacción
                Fecha
                Día de la semana
                Tiempo
                Tipo de tarjeta
                Modo de entrada
                Importe
                Tipo de transacción
                Grupo de comerciantes
                País de la Transacción
                Dirección de envío
                País de residencia
                Género
                Edad
                Banco
                Fraude

**Modelos(s) seleccionado(s)**

1) Arbol de decision: Este tipo de modelo permite realizar predicciones con comportamientos complejos, lo cual es crucial para este tipo de problematica, ya que los fraudes a las tarjetas de creditos se pueden desarrollar con una gran variedad de metodos y patrones. Ademas, los arboles de decision permiten visualizar el proceso de toma de decisones y entender las variables más relevantes, lo que nos va servier para clasificar si la transaccion es fraudilenta o no.

2) random forest: Este modelo es capaz de predecir comportamientos complejos al igual que el anterior, sin embargo cuenta con la ventaja de controlar el overfiting que se tiende a generar en los modelos de arbol de decision y tiene un mejor rendimiento con dataset con ruidos. Ademas, permite conocer de forma mas eficiente la importancia del resto de variables para la prediccion de fraudes, lo que nos permitira comprender cuales son los principales metodos utilizados para realizar fraudes.
        

Los métodos de decisión tree y random forest son modelos de clasificación con aprendizaje supervisado, los cuales nos serán de mucha utilidad para poder detec-tar los fraudes de forma eficiente, reduciendo tanto los falsos positivos como los falsos negativos.

**Árbol de Decisión**

Ventajas:

- Fácil de interpretar y visualizar.

- Útil para entender la lógica del modelo y la relevancia de las variables.

Limitaciones:

- Tiende a sobreajustarse a los datos de entrenamiento.

- Menor capacidad de generalización comparado con modelos más robustos.

**Random Forest**

Ventajas:

- Mejor capacidad predictiva que un solo árbol.

- Reduce el riesgo de overfitting al combinar múltiples árboles.

- Maneja bien datos con muchas variables y relaciones no lineales.

- Permite estimar la importancia de cada variable en la predicción.

Limitaciones:

- Menos interpretabilidad que un árbol único.

- Mayor costo computacional.


https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.StratifiedKFold.html

data set https://www.kaggle.com/datasets/anurag629/credit-card-fraud-transaction-data/data# p_ia


# Implemetacion
1. Carga del Dataset
Se utilizó el paquete `pandas` para cargar el archivo `CreditCardData.csv`. La primera inspección permitió observar la estructura general del conjunto de datos, como el número de columnas, tipos de datos y valores nulos. Del cual, pudimos obtener la siguiente informacion 
- Se observaron 16 columnas con datos mixtos: numéricos y categóricos.
- La variable objetivo es 'Fraud', con un desbalance del 7.2% de fraudes.

2. Exploración y Limpieza de Datos
Se revisó la presencia de valores nulos con `df.isnull().sum()` y se identificaron columnas con valores como 'unknown', que fueron tratadas como `NaN` y luego imputadas según el tipo de variable. También se aplicó la conversión de identificadores (ID) a valores enteros. Ademas, se elimino simbologia que acompañaba a los datos numericos de interes, como lo son el simbolo £ de la columna 'Amount', y el # de la columna Transaction ID, para ser pasados a datos enteros flotantes.

3. Análisis Exploratorio (EDA)
Se graficaron variables categóricas como Gender, Entry_Mode, Time_of_day y Card_Type para entender su distribución. Este paso permitió identificar desbalances y relaciones entre variables y la clase objetivo Fraud. Para realizar las graficas correspondientes y se separaron los datos en numericos y de categoricos, pero considerando 5000 instancias debido a la sobrecarga del entorno. 

4. Feature Engineering
Las variables categóricas fueron recodificadas manualmente. t_internacional la cual nos permite saber si la transaccion se realizo desde un pais distinto al de recidencia, r_hora el cual sirve para conocer el horario al cual se realizaron los movimientos, comparacion_direc sirve para saber si el pais de la tienda corresponde al pais de residencia. Para preparar estas columnas para aplicar el modelo, se transformaron a variables numericas, t_internacional y comparacion_direc quedaron con valores bopleanos (0 y 1), mientras que r_hora tomara el valor 0 si r_hora = 'Mañana', 1 si r_hora = 'Tarde', y tomara el valor 2 si r_hora = 'Noche'.

5. Divir datos en entrenamiento y testing
Una vez identificadas las columnas que consideramos importantes para identificar los fraudes, podemos separar los datos en conjunto de entrenamiento y de testing, donde X contendra contenida las columnas Amount, Age, t_internacional, r_hora y comparacion_direc. Mientras que Y contendra la columna de clasificacion de nuestro interes, el cual es fraude.
Posteriormente Procedemos a separar los datos, donde el 70% sera para el training y el 30% para el testing, finalizamos este punto escalando los datos, esto se realiza para que todos los datos se encuentren en una unidad de medida unica, de manera que se puedan relacionar de forma adecuada sin perder su importancia.

6. Aplicar modelo
Primero se aplicaco un modelo de Desicion Tree, donde se aplico un balanceamiento de los pesos de las clases con la finalidad de que el modelo mejore la precision en la deteccion de fraudes, debido a que esta clase cuenta con muy pocos datos en comparacion a las transacciones legitimas, lo cual podria haber provocado que el modelo clasificara todo como transaccion legitima y aun asi manteniendo un buen acurracy. El otro modelo que se aplico fue un random forest, al cual no se le aplico balanceamiento de las clases, debido a que al aplicar el balance nos entregaba resultados peores a los obtenidos normalmente. Ademas, se aplicaron versiones controladas de ambos modelos, donde se limitaron la cantidad de nodos, se puso una cantidad base de hojas a tener, entre otros parametros controlados.

=======
# Interpretacion
Sabemos que los fraudes en tarjetas de creditos son acciones que son bastantes perjudiciales para las empresas que ofrecen estos servicios, ya que generan una serie de problemas como la desconfianza de sus clientes, la perdida de dinero, entre otros. Por lo que, para las instituciones financieran es de gran importancia poder detectar este tipo de transacciones cuanto antes para poder tener una respuesta inmediata, es por eso que desarrollar un modelo de clasificacion que sea capaz de predecir las transacciones fraudulentas es una gran herramienta para estas empresas, que es lo que buscaba crear el modelo desarrollado en este trabajo. Sin embargo, la gran diferencia entre las clasificaciones representa un desafio, ya que se debe establecer bien la prioridad de la empresa, es decir, si estos priorizan detectar los fraudes a pesar que pueda generar que clasifiquen como fraude a transacciones legitimas o si es mejor detectar los fraudes pero minimizando los falsos negativos. 




Con los resultados obtenidos logramos notar que todos los modelos tuvieron resultados muy buenos en cuanto a clasificar las transacciones legitimas. por otro lado, los resultados al clasificar las transacciones fraudulentas en los modelos de Arbol fue moderada, y en los modelos de random forest mejoro considerablemente. las metricas resultantes de clasificar fraude son las siguientes:

| Modelo            | Acurracy| Precision | Recall | F1_score|
|:-----------------:|:-------:|:---------:|:------:|--------:|
| Arbol             |  95.9%  |   72.9%   |  71.2% |  72.1%  |
| Arbol controlado  |  95.9%  |   72.9%   |  71.2% |  72.1%  |
| Random forest     |  96.7%  |   80.8%   |  72.2% |  76.3%  |
| RF controlado     |  97.5%  |   86.4%   |  78.5% |  82.2%  |

https://scikit-learn.org/stable/modules/ensemble.html#forests-of-randomized-trees
dd