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

        Modelos(s) seleccionado(s)

            1 Arbol de decision ya que sirve como linea base proque  más facil de interpretar, ademas permite visualizar el proceso de toma de decisones y entender las variables más relevantes , nos va servier para clasificar si la transaccion es fraudilenta o no

            2 random forest tambien podemos usarlo ya que contiene multiples arboles de decision y esto aumenta la capacidad predictiva, ademas es robusto contra el overfiting y tiene mejor rendimiento ante los dataset con ruidos y que sean complejos(muchas variables).

        

ls

data set https://www.kaggle.com/datasets/anurag629/credit-card-fraud-transaction-data/data# p_ia
