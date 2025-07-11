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
Se utilizó el paquete `pandas` para cargar el archivo `CreditCardData.csv`. La primera inspección permitió observar la estructura general del conjunto de datos, como el número de columnas, tipos de datos y valores nulos.
2. Exploración y Limpieza de Datos
Se revisó la presencia de valores nulos con `df.isnull().sum()` y se identificaron columnas con valores como 'unknown', que fueron tratadas como `NaN` y luego imputadas según el tipo de variable. También se aplicó la conversión de identificadores (ID) a valores enteros.
3. Análisis Exploratorio (EDA)
Se graficaron variables categóricas como Gender, Entry_Mode, Time_of_day y Card_Type para entender su distribución. Este paso permitió identificar desbalances y relaciones entre variables y la clase objetivo Fraud.
4. Feature Engineering
Las variables categóricas fueron recodificadas manualmente. t_internacional, r_hora,comparacion_direc

Cris ayudame a profundizar cuando tengas tiempo ;(


https://scikit-learn.org/stable/modules/ensemble.html#forests-of-randomized-trees