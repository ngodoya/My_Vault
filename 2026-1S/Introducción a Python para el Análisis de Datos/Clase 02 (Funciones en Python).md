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

Retorna una lista de elementos desde 0 y hasta el parámetro que se envíe dentro de los paréntesis, aunque la mejor definición que se le puede dar es `range(inicio, final, pasos)`importante recordar que python suele tomar rel entero previo al final, si solicito un `range(10)`y lo imprimo en un for de una lista, me devolvera los números de 0 al 9.
## Funciones ajenas
A veces las funciones predeterminadas de python no suelen ser suficiente para trabajar en nuestro contexto, en este punto podemos acceder a algo conocido como **Librerias** y importar estas funciones (usualmente son clases) y ahora si aprovecharlas en nuestro código, una de las mayores ventajas de python frente a lenguajes como R o Julia es su libreria y comunidad constante, la cual ofrece muchas soluciones.
```python
import datetime as dt #Importar todas las funciones especificas
from datetime import datetime # Importar funciones especificas
```
Estas funciones tienen sus propias librerias y para ser instaladas se hacen por medio de la libreria `pip`, en la terminal de linux se pueden instalar como:
```bash
python -m pip install mi_libreria
# entorno virtual
python -m venv mi_entorno
source mi_entorno/bin/activate

```
Aunque para hacer esto no olvide instalar su entorno virtual, `pip`es el gestor de paquetes de python.
## Listas por comprensión (list comprehension)
Los creadores de python se dieron cuenta que crear listas en versiones antiguas resultaba incomodo, para ello en vez de utilizar ciclos for, crear listas aparte y luego hacer el append python agrego una estructura bastante util para resumir estos procesos.
![[Pasted image 20260704094919.png]]
## Funciones Lambda
Unas funciones anónimas (no tienen nombre a menos que se les asigne en una variable) de python para crear funciones rápidas que no tengan mucho impacto en el código, solo pueden ejecutar **una sola expresión matemática o lógica**
>[!python] **Note:** No es muy recomendable usarlas si son funciones recursivas dentro del código (funciones que se van a utilizar mucho)

Las ventajas es que se pueden definir rápido y son utiles para devolver valores que se vayan a utilizar una vez en el código, a diferencia de una función tradicional (`def`), las expresiones lambda devuelven el resultado de forma implícita ; no requieren (ni permiten) escribir la palabra `return`

Tags: #PEP8

