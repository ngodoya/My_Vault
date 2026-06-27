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

Tags: #venv #notebook #Latex 