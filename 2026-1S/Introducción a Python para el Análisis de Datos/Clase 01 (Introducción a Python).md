Google Collaboratory utiliza el concepto de maquinas virtuales para usar #notebook (Cuadernillos de Trabajo), maquinas virtuales que nos presta Google para realizar nuestros cambios, lo ideal es descargar los archivos y ejecutarlos de manera propia con una copia, para evitar perder progresos.
# Markdown
Código hecho para la Wikipedia, contribuir y escribir textos, donde se utiliza una sintax y comandos similares al #Latex, se renderiza a traves de celdas en un cuadernillo, resultan muy utiles al mostrar hipervinculos, negrilla, explicaciones detalladas con ecuaciones, enriquece de manera muy bonita el aprendizaje y abstracción de la información en nuestro cuadernillo (puede utilizar incluso syntax de ```HTML5```). La idea de los cuadernillos es enriquecer y explicar, no solo poner código.
# Python y Notebook
Python como Lenguaje es un lenguaje de programación muy completo, cumple los 3 paradigmas de la programación (Imperativo, Funcional y Orientada a Objetos) como ya ha visto en otros cursos o momentos, Python es sencillo, rápido y eficaz, pero no es perfecto, depende del problema al que se quiera afrontar.
## Frente a otros lenguajes
Para el mundo de la ciencia de datos Python es ideal, pero no perfecto como se mencionó previamente, lo ideal es tener una idea sobre como manejar varios lenguajes y afrontar el problema, la ventaja de Notebook es que nos permite emular 3 Lenguajes super valiosos para el mundo de la ciencia de datos (R, Julia y Python). Aprender cada uno puede ser agotador pero vale la pena.
Si desea reforzar sus conocimientos en cualquier lenguaje el siguiente enlace le puede ser de interes: [w3schools](https://www.w3schools.com/).

>[!Funfact]- Dato Curioso:
>Ju Julia
Py Python
te (creo que no significa nada)
R R
**Ju**Py**te**R**
# GPU vs CPU vs TPU
En analisis de dato las GPU pueden acelerar el procesamiento gráfico (no solo en el gaming) para el mundo del análisis de datos, usualmente la CPU es bastante limitada en lo últimos momentos del renderizado. El mundo del hardware totalmente aparte, pero no significa que no sea influyente en nuestro análisis de datos. jeje, las TPU son excesivamente complejas de conseguir, pero modelos sumamente modernos.
# Interfaz Notebook
![[Pasted image 20260627084509.png]]

Jupyter Permite analizar y conocer el flujo y la información de los cuadernillos activos, traer datasets, incluso encontrar conjuntos de datos, Google Collaboratory puede traer ciertas ventajas frente a las extensiones
## Números

Es el tipo de datos que más iremos a usar y puede ser de cualquiera de éstos subtipos:

* int: entero
* long: entero long
* float: punto flotante
* complex:	complejo
* bool: booleano
Python infiere los tipos de datos, a diferencia de otros lenguajes donde los datos deben ser definidos de forma manual (cosa que puede ser una ventaja)
### Operaciones
Python trae las clásicas operaciones que se suelen enseñar en primaria/bachiller (+, -, $\times$, $\div$,$x^n$ ), manejando la presedencia de los operadores, es importante recalcar que esta presedencia se puede manipular utilizando los $()$, la operación modulo da el residuo de la división entera, Ej: $4\%5=4$ , $5\%4 = 1$  .
La asignación en python se muestra como:
```python
x = 7 #x es igual a 7
y = 2
z = x + y 
```
## Datos Boleanos
VIenen del algebra booleana, sep ueden utilizar como operaciones de modulo 2, True, Falseo o 0 y 1.
## Cadenas
`'uso del caracter de escape para escribir el caracter de comilla simple\' dentro de una cadena con comilla simple'`
podemos utilizar los índices de las cadenas, s sub, se escribe como s[0] (note que en python empezamos por el indice 0), podemos encontrar la posición de cada carácter con su indice (cosa que puede ser díficil si no vemos la palabra).
### Troceados de cadenas (Slicing)
Para tomar un subconjunto de elementos de la cadena inicial se puede utilizar el indice en forma de rango:
```python
cadena[inicio:fin:paso]
```
El paso final no sera tomado en cuenta, python siempre va al entero anterior.
el paso no necesariamente tiene que ser un entero positivo, puede ser un entero negativo, dando pasos hacía atrás, util para encontrar palindromos, cuando los pasos son negativos el inicio es -1, no 0.
>[!abstract]- Shell
>Cuando solicitamos a notebook que ejecute una comando shell (bash) podemos hacerlo poniendo ```python !python --version```
### Listas
Son secuencias de elementos que pueden pertenecer a cualquier tipo de dato. Estas listas guardan un órden que está definido el índice, incluso podemos tener Listas dentro de listas, dentro de listas... y así indefinidamente, los métodos más relevantes son los siguientes.
**Métodos:**
- `append`El método añade un valor a la lista en una nueva posición (existe un nuevo -1 en los indices)
- `remove()` elimina el primer elemento solicitado que encuentre.
- `pop()`elimina pero podemos enviar ese valor a una nueva variable:
Ejemplo: 
```python 
  # Eliminar un elemento de la lista por su posición y retorno el dato
		eliminado = my_list.pop(1)
		my_list
```

el Slicing también aplica para los valores de una lista, así mismo a los valores internos de una lista,

>[!Example]- Ejercicio
>Recuperar la cadena "hola" de la siguiente lista: `["a",2,3,["1","2"],["hola",[0,2,"encuentrame"]]]`

## Diccionarios
Se utilizan llaves para definirlos, permiten manejar parejas clase y valor, lo cual resulta util para llamar un tipo de dato, son conjuntos `sets`dentro de python. ***Tip:*** Las llaves es recomendable organizarlas por el mismo tipo de dato.
Los mismos no manejan indices.
Ejemplo:
```python
dic = {'key1': 10,'key2': 'pato'}
dic = {(0,1): 25, (1,0): 10} # Utilizando Tuplas como llaves
```
También podemos anidar diccionarios dentro de diccionarios, similiar a las listas.
- `keys`Trae las llaves del primer nivel del diccionario, similar a `values`
## Tuplas
Son como listas, pero inmutables, no hay mucho que agregar, son poderosas para las redes neuronales del machine learning
## Conjuntos
Los sets pueden verse desde las propiedades matematicas, no se pueden repetir cosas en un conjunto (no existe la multiplicidad), así mismo podemos realizar todas la operaciones que conocemos de los conjuntos, union (|), intersección (&), la diferencia entre los conjuntos o incluso operaciones más complejas (recordar los diagramas de #Venn)
## Operadores condicionales
Los operadores  de este tipo resultan utiles para comprobar valores o desigualdades, sabiendo si son verdaderas o falsas, suelen tener en cuenta el orden de indexacion de las listas, los operadores pueden utilizarse para saber cuando debe de parar un programa o incluso cuando debemos tomar otra ruta (diagramas de flujo). Se combinan con las tablas de la verdad, casos donde vemos los condicionales de and (disyuncion), or (conjuncion), negación, condicionalidad y bicondicionalidad, existe otro operador conocido como **XOR** el cual es solo verdadero cuando uno y unicamente una de las proposiciones es verdadera.
![[Pasted image 20260627112615.png]]
## Control de Flujo
Cómo se mencionó previamente, al realizar  código es importante utilizar condicionales para saber que secciones del código se van a correr, para ello existen las palabras reservadas **if, elif, else**
>[!Python]- Code
>```python
>if 1 > 2:
  print("Si")
  print("SiSi")
  print("NoNo")
print("SiSiSi")```

Los previamente descritos se pueden leer como, si, si no se cumplio x pero se cumple y, si no se cumplio ninguna, respectivamente, parte vital del código es comprender correctamente estos casos y evaluarlos (desglosar y abstraer un problema).
***Tip:*** Si se cumple uno de los casos, automaticamente python ignorara los siguientes elif o else.
### Ciclos
Existen dos ciclos en python, los **For** y los **While**,en el caso del For el código dentro del ciclo se repetira la cantidad de veces que se establezca, el while es un poco más peligroso, ya que dependera de un condicional para ejecutar el codigo, hasta que este condicional sea falso o verdadero (dependiendo de cuando queremos que pare) el código no se detendra.
Es util combinarlo con la función `range(inicio, fin, paso)`, ambos pueden realizar el mismo tipo de tareas (dependiendo de la que se necesite uno puede ser más fácil y otro más complejo).
>[!Example]- Fibonnaci Code
># Ejercicio
Generar los primeros N numeros de la secuencia de Fibonacci utilizando la estructura repetitiva **for** y la estructura repetitiva **while**
$f(n) = 0, 1, 1, 2, 3, 5, 8, 13, ...$

>[!python] Solución
>```python
>n = 8
>val = [0, 1]
>for k in range(2, n):
i = val[k - 2]
j = val[k - 1]
val.append(i + j)
print(val)
>```

Otra Solución puede ser obtenida utiliza la igualda en python, una igualdad de varias variables, donde se hacen intercambios de información al tiempo.
```python
n = 10
a, b = 0.0, 1.0
for k in range(2, n):
    a, b = b, a + b
    print(b)

```


Tags: #venv #notebook #Latex #Venn 