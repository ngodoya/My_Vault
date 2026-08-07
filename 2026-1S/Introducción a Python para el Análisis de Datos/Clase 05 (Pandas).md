## ¿Qué es pandas?
Es una librería de análisis de datos que se compone de una serie de estructuras de datos con funcionalidades para limpiar, analizar y preprocesar los datos para tareas siguientes al análisis.

![[download.png]]
## Importando pandas
Pandas se puede importar de la siguiente manera. Se utiliza el nombre pd por facilidad de manejo.
```python
!pip install pandas # Instalar
import pandas as pd
pd.__version__ # Conocer la versión actual de pandas
```
## Ejemplos de estructuras de datos
### Series
Una serie es un #arreglo unidimensional con un índice correspondiente a cada posición del arreglo. Por ejemplo, el listado de jugadores de un equipo, donde el arreglo tiene los apellidos de los jugadores y el índice el número del jugador.
Ejemplo:
```python
seleccionColombia = pd.Series(
    ['Ospina', 'Zapata', 'Falcao', 'Cuadrado', 'Rodriguez'],
    index=[1, 2, 9, 11, 10])
```
>[!pandas] Como se puede observar con los jugadores Cuadrado y Rodriguez, los índices no tienen que estar necesariamente ordenados. La serie se puede imprimir escribiendo su identificador.

Una serie se puede generar sin conocer los índices y Pandas los generará automáticamente con valores desde cero hasta el tamaño de la lista menos uno (n-1). En el caso de la misma serie:

| 0   | 0         |
| --- | --------- |
| 0   | Ospina    |
| 1   | Zapata    |
| 2   | Falcao    |
| 3   | Cuadrado  |
| 4   | Rodriguez |
>[!tip] Las series tambien pueden ser definidas desde diccionarios:
>```python
>dict_selcol = {1:'Ospina', 2: 'Zapata', 9: 'Falcao', 11: 'Cuadrado', 10: 'Rodriguez'}
print(dict_selcol)
>```

En este caso los indices son las llaves del diccionario, el método Series facilita convertir este diccionario en un arreglo, además de ello podemos ver funciones para obtener los primeros valores del arreglo o las ultimas, estas son:
- `head(n)` Llama los primeros $n$ valores de la series o el #DataFrame
- `tail(n)` Llama los últimos $n$ valores de la series o el #DataFrame.
### DataFrame
Un DataFrame es una estructura de datos que almacena la información como una tabla ordenada por filas y columnas. Cada fila representa un objeto y cada columna la información correspondiente a una característica de los objetos.

Un DataFrame también posee índices por cada fila, que pueden ser dados o generados automáticamente. Cada columna del DataFrame es una **serie**, donde el valor del índice corresponde con los valores de índice que tiene el DataFrame.

Por medio de un diccionario vamos a crear un dataframe, donde las llaves son los nombres de las columnas y los valores son la lista de valores que tienen las características.

Por ejemplo, para hacer un DataFrame con el equipo de fútbol anterior, pero agregando estatura y peso, podemos hacerlo de la siguiente manera:
>[!pandas] DataFrame
>```python
>dict_caracteristicas = {'apellido':['Ospina', 'Zapata', 'Falcao', 'Cuadrado', 'Rodriguez'],
>'altura':[183.0,187.0,177.0,179.0,180.0],
>'peso':[80.0,82.0,72.0,72.0,75.0]}
>seleccionColombia = pd.DataFrame(dict_caracteristicas,index=[1, 2, 9, 11, 10])
>```

En este caso el Index de cada columna corresponde a los dados previamente (los números del jugador).
Al imprimir el DataFrame, podemos observar que su estructura es similar a la de un documento en Excel, donde el índice (que no tiene nombre de columna) es el número del jugador.

|     | apellido  | altura | peso |     |
| --- | --------- | ------ | ---- | --- |
| 1   | Ospina    | 183.0  | 80.0 |     |
| 2   | Zapata    | 187.0  | 82.0 |     |
| 9   | Falcao    | 177.0  | 72.0 |     |
| 11  | Cuadrado  | 179.0  | 72.0 |     |
| 10  | Rodriguez | 180.0  | 75.0 |     |
>[!Example]  Ejercicio
Crear un data frame que modele la información de 10 mascotas


Tags: #arreglo #DataFrame 