# Excepciones Clase 12:
En resumen una excepción es un evento inesperado que ocurre durante la ejecución de un programa **(Ej: División por 0)**, problemas debido a tiempo de ejecución, cosa que complica debido a que python es un lenguaje interpretado, el mundo es cruel pero hay formas de adaptarse.
>[!Example]- Ejemplo:
>Calcular promedio
>def calcular_promedio(numeros):
>  total = 0
>  for numero in numeros:
>    total += numero
>  return total / len(numeros)
>promedio = calcular_promedio([1, 2, 3, "4"])
>print(f"El promedio es: {promedio}")

Recibe cosas que no son posible de promediar (no tiene sentido promediar un carácter), para ello existe la solución de:
```python
try:
  promedio = calcular_promedio([1, 2, 3, "4"])
  print(f"El promedio es: {promedio}")
except TypeError:
  print("Error: Se introdujo un valor no numérico.")
```
Agarramos el error y solicitamos que intente realizar la operación, si no es capaz de realizarlo, python no descompone el programa, continua con lo que viene, aquí planteamos la pregunta, cómo gestionamos los errores?

---
### Ejemplos
- Cómo valido que una persona ingrese solo caracteres?
- Indices que no existen?
- Errores de Runge-Kutta
recordar el zen de python, No olvidarlo ``(import this)``
## Estructura `try - except - finally
Todo lo que se encuentre dentro del bloque ``try:`` permite agrupar un conjunto de instrucciones en un bloque, si se levante un error ***(excepción)*** evita que el programa se detenga, except es quien da la cara si se levanta el error
>[!Note]- Except y la descomposición de escenarios
>En ningún momento se limita a que except sea solo 1, puede tener multiples excepts
>

>[!Note] Finally
>Es **opcional**, se ejecuta SÍ O SÍ , siempre haga incluso aunque no pase el except o el try, combinar 3 cosas, forza a que el programa termine (comprende el sistema y lo descompone en mejores ideas)

Ejemplo cuando conocemos el error:
```python
def dividir(numerador, denominador):
  return numerador / denominador

try:
  resultado = dividir(10, 0)
  print(f"El resultado de la división es: {resultado}")
except ZeroDivisionError as error:
  print(f"Error: {error}")
```
Note que podríamos dejar `ZeroDivisionError` como `Exception` esto implica que no sabemos bien lo que estamos corriendo, pero lo capturamos con un alías, eso implica que guardamos el error aunque no conozcamos bien, *Ojo* podríamos dejar `Except` solo, cosa que es una mala práctica, debido a que ``Except`` es una clase.   ``print(f"Error: {error.__class__}")``

## Uso del `Raise`
Levantar excepciones de forma programatica, ejemplo: dentro de las funciones.
```python

def obtener_elemento(lista, indice):
  if indice < 0 or indice >= len(lista):
    raise IndexError("Índice fuera de rango.")
  return lista[indice]

try:
  elemento = obtener_elemento([1, 2, 3], 4) # note que el error se levante
  print(f"El elemento en la posición 4 es: {elemento}")
except IndexError as error:
  print(f"Error: {error}")
```
raise consigue el error en el punto en el que lo consigue y luego lo manda a la excepción, para que esta mismo puedo capturarlo.
## Uso del finally
Estudialo... la verdad no entendí bien como se aplico en el ejemplo.
### Excepciones comunes en python

| Excepción         | Explicación                                                                                       | Manejo                                                                                                                                                                                                                              |
| ----------------- | ------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| TypeError         | Ocurre cuando se intenta realizar una operación incompatible con los tipos de datos involucrados. | Verificar los tipos de datos involucrados en la operación y asegurarse de que sean compatibles. Si es necesario, convertir los tipos de datos antes de realizar la operación.                                                       |
| ValueError        | Ocurre cuando se proporciona un valor incorrecto para una operación específica.                   | Validar los valores de entrada antes de realizar la operación. Asegurarse de que los valores sean del tipo correcto y cumplan con los requisitos específicos.                                                                       |
| NameError         | Ocurre cuando se hace referencia a una variable o nombre que no ha sido definido.                 | Verificar que la variable o nombre haya sido definido antes de utilizarlo. Si es necesario, declarar la variable o nombre antes de usarla.                                                                                          |
| KeyError          | Ocurre cuando se intenta acceder a una clave inexistente en un diccionario.                       | Verificar si la clave existe en el diccionario antes de acceder a ella. Utilizar el método `get()` del diccionario para obtener el valor asociado a una clave, o especificar un valor predeterminado para la clave inexistente.     |
| IndexError        | Ocurre cuando se intenta acceder a un elemento de una lista con un índice fuera de rango.         | Verificar que el índice esté dentro del rango válido de la lista antes de acceder al elemento. Utilizar el método `len()` para obtener la longitud de la lista y el método `range()` para generar una secuencia de índices válidos. |
| FileNotFoundError | Ocurre cuando se intenta abrir un archivo que no existe.                                          | Verificar que la ruta del archivo sea válida y que el archivo exista antes de intentar abrirlo. Utilizar la función `os.path.exists()` para verificar si un archivo existe.                                                         |
| ImportError       | Ocurre cuando se intenta importar un módulo que no existe o no está disponible.                   | Verificar que el módulo esté instalado correctamente y que la ruta de importación sea válida. Utilizar la función `importlib.util.find_spec()` para verificar si un módulo existe.                                                  |
| ZeroDivisionError | Ocurre cuando se intenta dividir por cero.                                                        | Validar el denominador antes de realizar la operación de división. Asegurarse de que el denominador no sea cero.                                                                                                                    |
| AttributeError    | Ocurre cuando se intenta acceder a un atributo de un objeto que no lo posee.                      | Verificar si el atributo existe en el objeto antes de acceder a él. Utilizar la función `hasattr()` para verificar si un objeto tiene un atributo específico.                                                                       |
## Crear nuevos errores
Es requisito heredar de `Exception`, siendo una clase abstracta, aplicando lo que necesitamos para  la clase en especifico y el problema en especifico, mucho raises en un solo except, prevenimos toda los posibles escenarios donde fallamos, propias clases con excepciones y levantarlas a conveniencia **OP**.




Tags: #try #finally
