# Funciones

Una función, es la forma de agrupar expresiones para realizar  determinadas acciones.
La ejecucución de éstas depende que sea llamado el bloque que las define.
## Definición de Funciones

En Python, la definición de funciones se realiza mediante la instrucción def más un nombre de función descriptivo.
La definición de la función finaliza con dos puntos, la documentación de una función va en triple comilla (doble o simple), esto es según los estandares del #PEP8 (:)
```python
def my_func(param1="Hola Funciones"):
    """
    Aquí irá la documentación (docstring)
    param1: este parámetro es..
    Esta función return
    """
    print(param1)
```
>[!python] **Note:** Para código Pythonico es recomendable dejar lasa funciones en *Snake_case*

Las funciones pueden recibir y devolver parámetros, pasar parámetros es una forma de que tome los  valores internos y haga lo que tiene que hacer con los parámetros dados, se puede ver como una secuencia de código guardada en la memoria del programa, al ejecutarse no pasara nada, la utilidad es que la primera vez que se ejecuta es una forma de declararla y luego podremos invocarla y utilizar todas sus propiedades, si tenemos dudas sobre una función y su uso es útil la propiedad `my_func?`, nos dara acceso a toda la información que el programa tiene de la función. 
Ejemplo:
```text
Signature: my_func(param1='Hola Funciones')
Docstring:
Aquí irá la documentación (docstring)
param1: este parámetro es..
Esta función return
File:      /tmp/ipykernel_19265/1858793545.py
Type:      function
```
## Return
Las funciones en python son envidiosas, lo que crean dentro de ellas se conoce como variables *Globales* y *Variables Locales* una forma de afrontarnos frente a este conflicto es utilizar la palabra reservada `return`para solicitar a la función que nos devuelva el valor solicitado, es útil definir en la documentación en 3 partes.
1. Utilidad o proposito de la función, Ejemplo: Está función cálcula el cuadrado de un número.
2. Variables que recibe, Ejemplo: x: número que se desea calcular el cuadrado.
3. Valores que retorna, Ejemplo x_: Cuadrado del número solicitado
## Range()

Retorna una lista de elementos desde 0 y hasta el parámetro que se envíe dentro de los paréntesis, aunque la mejor definición que se le puede dar es `range(inicio, final, pasos)`importante recordar que python suele tomar rel entero previo al final, si solicito un `range(10)`y lo imprimo en un for de una lista, me devolvera los números de 0 al 9



Tags: #PEP8

