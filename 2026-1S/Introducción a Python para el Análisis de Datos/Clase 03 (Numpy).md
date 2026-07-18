**NumPy: Librería de álgebra lineal para Python.**

NumPy es el paquete fundamental para la computación científica con Python. Contiene, entre otras cosas:
* una poderoso tipo de datos de matrices N-dimensionales: arreglos numpy
* funciones sofisticadas (broadcast)
* herramientas para integrar código C/C ++ y Fortran
* funcionalidades útiles de álgebra lineal, transformada de Fourier, números aleatorios

Además de sus usos científicos obvios, NumPy también se puede usar como un contenedor multidimensional eficiente de datos genéricos. Se pueden definir tipos de datos arbitrarios. Esto permite a NumPy integrarse de manera rápida y sin problemas con una amplia variedad de bases de datos.

NumPy también es muy rápido (ya que usa librerías de lenguaje C). Para ver más información acerca de por qué usar Arreglos en lugar de Listas, ver [este post de StackOverflow](http://stackoverflow.com/questions/993984/why-numpy-instead-of-python-lists).
## Instalación

**Se recomienda instalar Python usando la distribución Anaconda para asegurarse que todas las dependencias (como las librerías de álgebra lineal) se instalarán mediante el uso del comando "conda install". Si tiene Anaconda, instale NumPy simplemente escribiendo el siguiente comando en una terminal:**
    
    conda install numpy
    
**Si no tiene la distribución Anaconda, ejecute el comando "pip install numpy". Si no tiene éxito, ver: [la documentación oficial de Numpy para más instrucciones de instalación.](http://docs.scipy.org/doc/numpy-1.10.1/user/install.html)**
## Arreglos NumPy

Los arreglos de NumPy serán la principal funcionalidad que usaremos durante el curso.

**Tipos de arreglos:**
* Vectores: 1-d
* Matrices: 2-d (aunque podrían tener una sola fila o una sola columna)
## Creación de Arreglos NumPy (Arrays)

### A partir de Listas de Python

Podemos crear un Array conviertiendo una lista o lista de listas en un arreglo de NumPy:
```python
lista = [0,2,3]
np.array(lista) 
arr*3 # Multiplicación por escalar
```
Para esto relevante recordar todas las aplicaciones que teníamos en el álgebra lineal, la propiedad de Multiplicar por un escalar esta definida por:
$$\lambda(a_1,a_2,\cdots,a_n)=(\lambda a_1,\lambda a_2,\cdots,\lambda a_n)$$
Note que $\lambda \in \mathbb{R}$ siendo una constante puede entrar y salir de los vectores (arreglos)
# Funciones para generar arreglos

Existen varias funciones para generar Arreglos:
## Arange

Funciona de forma similar al método "range" de Python pero devuelve un arreglo.
`np.arange(0,11,2)`
## Ceros y unos (zeros/ones)

Generan arreglos de ceros (zeros) y unos (ones), pueden generar Vectores (Columna o FIla) y Matrices $nxm$.
```python
np.zeros((2,3), dtype='int')
```
podemos definir el de numero en la matriz, a veces es conveniente forzar el tipo de caracter para evitar errores numericos o de redondeo por parte de Python.
## Linspace
Retorna un vector (arreglo de una dimensión) desde un número (primer parámetro) hasta otro (segundo parámetro) separados entre si por la misma distancia. El número de elementos está determinado por el tercer parámetro.
```python
np.linspace(a, b, n)
np.linspace(0,10,100)
```
la cantidad de elementos se define como $$\dfrac{b-a}{n}$$ donde $n$ se define como un número exclusivamente natural $n \in \mathbb{N}$
## Repaso de conceptos básicos de Álgebra Lineal
https://stanford.edu/~shervine/l/es/teaching/cs-229/repaso-algebra-lineal-calculo
## Eye

Crea una matriz identidad del tamaño indicado en el argumento, una forma de crear la función que nos entre una identidad puede ser la siguiente:
```python
def eye(n):
    A = np.zeros((n, n), dtype="float")
    for i in range(n):
        A[i, i] = 1.0
    return A
# Analogos
eye(4)
np.eye(4)
```

>[!numpy]- **TODO**, absolutamente **TODO** es un vector en el mundo del análisis de datos, podríamos definir una **matriz** como un conjunto de **vectores** o sea de información aplicada en una colección de datos
# Generación de números y arreglos de números aleatorios

Los números aleatorios son importantísimos en computación. Como veremos, NumPy ofrece funciones para generar datos aleatorios simples y basados en algunas distribuciones estadísticas.
```python
# Sin argumentos se general un número aleatorio entre 0 y 1
np.random.rand() 
```
## Crear un arreglo de números aleatorios

Numpy también ofrece varias maneras de crear arreglos de número aleatorios:
### Seed
Semilla para números aleatorios
```python
np.random.seed(10)
```

### Rand

Crea un arreglo del tamaño dado y lo llena con una muestra aleatoria de números con una distribución uniforme en el rango $[0, 1)$.
```python
np.random.rand(7)  # Un array de 7 elementos 
# Si corrio la semilla anterior el resultado nunca cambiara, se aplica para TODOS los aleatorios que se calcules despues de correr la celda de la semilla
```
### Randn
Retorna un arreglo con una muestra de números aleatorios con una distribución normal (centrada en 0), a diferencia de rand cuya distribución es uniforme:
```python
np.random.randn(4,5)
```
Más info acerca de distribuciones de probabilidad en este [**enlace**](https://www.healthknowledge.org.uk/public-health-textbook/research-methods/1b-statistical-methods/statistical-distributions).
### Randint
Retorna números enteros aleatorios desde el primer parámetro (inclusive) hasta el segundo parámetro (excluido). Si tiene un tercer argumento, éste será el número de elementos que tendrá el arreglo de enteros aleatorios que retorna.
```python
np.random.randint(1,100,12)
```
## Atributos y manipulación de los arreglos

```python
arr = np.arange(6)
ranarr = np.random.randint(0,50,10)
ranarr2 = np.random.randint(0,50,(10,10))
```
## Shape: Forma del arreglo

Shape  es un atributo de los arreglos que indica las dimensiones del arreglo:
```python
arr.shape
ranarr2.ndim # da la dimension (en ejes) del objeto
```
## Reshape
Retorna un arreglo que contiene los mismos datos que el arreglo original pero con unas dimensiones nuevas, podemos pasar una  3x2 a una 2x3 o un arreglo 6x1 a un 2x3 (note que se mantiene la dimensión)
```python
arr.reshape(6, 1)
```
## Max, min, argmax, argmin

Estos métodos se usan para encontrar los valores máximos y mínimos en un arreglo. También, para encontrar los índices donde están ubicados mediante argmin/argmax.
## dtype

También es posible averiguar el tipo de dato del arreglo usando el atributo dtype:
## Importar directamente función de un módulo

Para evitar tener que llamar el módulo y luego la función, por ejemplo:

**np.random**

Se puede importar la función directamente.
```python
from numpy.random import randint
```
## NumPy Indices

En un arreglo el índice es la posición de la secuencia para cada uno de los elementos.
```python
vector1 = np.array([0,1,2,3,4,5,6,7,8,9,10])
print(vector1)
print('Elemento en posición 0: ', vector1[0])
```
### Arreglos uni-dimesionales Vectores

La forma más sencilla de seleccionar un elemento o un conjunto de ellos de un arreglo es muy similar a las listas de Python:
## Obtiene el elemento ubicado en el índice dado
```python
# Obtiene los elementos en el rango dado (sin incluir el límite superior)
vector1[1:5]
# Obtiene los elementos desde el inicio hasta el elemento en la posición 7
vector1[:7]
# Obtener desde una posición hasta el final del erreglo
print(vector1[5:])
print(vector1[5:11])
# Obtener desde la posición inicial y hasta la 8, cada 2 posiciones
vector1[0:8:2]
# Obtener todo el arreglo pero en órden inverso
vector1[::-1]
```
### Arreglos bi-dimensionales (Matrices)
```python
# Inicialización
arr2d = np.zeros((5,5))
for i in range(5):
    arr2d[i] = i

arr2d
# Tamaño de la fila 1
arr_length = arr2d.shape[1]

arr_length
#Obtener todos los elementos de la primera fila
print(matriz_a[0,:])
#Obtener todos los elementos de la primera columna
print(matriz_a[:,0])
```

### Arreglo n-dimensionales (Tensores)
```python
arr_3d = np.array(([[[5,10,],[20,25]],[[7,21],[7,28]]]))
print(arr_3d) # Matrices dentro de matrices
```

El formato general es **arr_nd[d1][d2][dn]** o **arr_2d[d1,d2,dn]**.

Por claridad, se recomienda la notación con coma.
## Broadcasting e Indexado Elegante
```python
c = np.zeros((3, 3))
print(c)
print(c.shape)
n = np.array([1, 2, 3])
print(n)
print(n.shape)
t = n + c  # Se expande la primera dimensión de n
print(t)
arr = np.arange(1,11)
print(arr)
# Asignar un valor dado a un rango de índices en un arreglo (Broadcasting)
arr[0:5] = 100

# Resultado
arr
arr[0::2] = -1

arr
# Troceado de arreglos
trozo_de_arr = arr[0:6]

# Resultado
trozo_de_arr
# Cambios
trozo_de_arr[:] = 99

#Show Slice again
trozo_de_arr
# Para obtener una copia, es necesario usar el método copy()
copia_arr = arr.copy()

copia_arr
```

>[!python] **OJO: los cambios también ocurren en el arreglo original!**
**Los datos no se copian, un "trozo" de un arreglo es simplemente una vista del arreglo original! ** Esto sirve para prevenir problemas de memoria!
### "Indexado elegante" (fancy indexing)

Se permite indexar filas o columnas enteras de una sola vez:
```python
arr = np.arange(10,21)
arr
# Obtener elementos también en cualquier orden
arr[[7,3,4]]
```
## Selección condicional

```python
#Validación elemento a elemento
indices_cond = arr > 3
print(indices_cond)
# Seleccion de elementos basados en alguna condición
arr[indices_cond]
arr[arr > 3]
#Usando condiciones más complejas
arr[(arr>=1) & (arr<=4)]
x = 2
arr[arr>x]
```
# NumPy  - Operaciones
## Aritméticas

Es posible hacer operaciones aritméticas entre arreglos; y también, entre arreglos y escalares. Se usan los operadores aritméticos tradicionales.
```python
v1 = np.array([2,10,10])
print(v1)
#Multiplicación vector por escalar
print(2*v1)
#Suma de dos vectores
v2 = np.array([1,2,1])
print(v1)
print(v2)
# suma y resta
v1+v2 
# multiplicación
v1*v2 #elemtento con elemento pero sin sumar Rn -> Rn
# división
print(v1/v2)

# En Python, la siguiente división retorna un error
1/0
# Sin embargo, en NumPy si dividimos arr/arr, obtendremos un Warning de división por cero, pero no se considera como un error!
# Se reemplaza por 'NaN' (Not a Number)

arr/arr
# 1/arr también produce un warning, pero no un error. En la división 1/0 se obtiene 'inf' (infinito)
1/arr
# Potencia
arr**3
```
>[!python] Diferencia con las listas de Python
## Operaciones Entre Matrices
El operador * multiplica los elementos uno a uno (NO es multiplicación matricial)
print(a * b)

## Multiplicación
### Multiplicación Vector-vector

Hay dos tipos de multiplicaciones vector-vector:

* **Producto interno:** Para $x,y \in \mathbb{R}^n$, se tiene que:
  $$x^T y = \sum_{i=1}^{n} x_i y_i \in \mathbb{R}$$
* **Producto diádico:** Para $x \in \mathbb{R}^m, y \in \mathbb{R}^n$, se tiene que:
  $$xy^T = \begin{pmatrix} x_1y_1 & \cdots & x_1y_n \\ \vdots & \ddots & \vdots \\ x_my_1 & \cdots & x_my_n \end{pmatrix} \in \mathbb{R}^{m \times n}$$

---

### Multiplicación Matriz-vector

El producto de la matriz $A \in \mathbb{R}^{m \times n}$ y el vector $x \in \mathbb{R}^n$ es un vector de tamaño $\mathbb{R}^m$, tal que:

$$Ax = \begin{pmatrix} a_{r,1}^T x \\ \vdots \\ a_{r,m}^T x \end{pmatrix} = \sum_{i=1}^{n} a_{c,i} x_i \in \mathbb{R}^m$$

Donde $a_{r,i}^T$ son los vectores fila y $a_{c,i}$ son los vectores columna de $A$, y $x_i$ son las entradas de $x$.

---

### Multiplicación Matriz-matriz

El producto de las matrices $A \in \mathbb{R}^{m \times n}$ y $B \in \mathbb{R}^{n \times p}$ es una matriz de tamaño $\mathbb{R}^{m \times p}$, tal que:

$$AB = \begin{pmatrix} a_{r,1}^T b_{c,1} & \cdots & a_{r,1}^T b_{c,p} \\ \vdots & \ddots & \vdots \\ a_{r,m}^T b_{c,1} & \cdots & a_{r,m}^T b_{c,p} \end{pmatrix} = \sum_{i=1}^{n} a_{c,i} b_{r,i}^T \in \mathbb{R}^{m \times p}$$

Donde $a_{r,i}^T, b_{r,i}^T$ son los vectores fila y $a_{c,j}, b_{c,j}$ son los vectores columna de $A$ y $B$ respectivamente.
## Otras Operaciones
```python
a = np.array([[0, 1, 2], [3, 4, 5]]) # arreglo 2 x 3
a.transpose()
a.sum()
a.sum(axis=1)
a.sum(axis=0)
```
## Funciones Universales con Arreglos

Numpy viene con muchas [funciones universales para arreglos](http://docs.scipy.org/doc/numpy/reference/ufuncs.html), las cuales son operaciones matemáticas que se pueden usar para efectuar una operación sobre el arreglo. Por ejemplo:
- Cuadraticas
- Logaritmicas
- Sin, cos, tan
- np.max: devuelve el valor máximo del arreglo
- np.argmax: devuelve el **índice** 
Ejemplo de iteraciones:
```python
# Iterar sobre el par de coordenadas x,y
a = np.array([[1,2],[3,4],[5,6]])
print(a)
for index, value in np.ndenumerate(a):
  print('index:',index,', value: ',value)
```
  **Consultar más info: https://docs.scipy.org/doc/numpy/user/quickstart.html**
  #Ejercicio: Multiplicación de Matrices

Escribe una función en Python que reciba dos matrices (listas de listas) y retorne su producto matricial.

**Instrucciones**:
* Crea una función llamada multiplica_matrices que tome como parámetros dos matrices A y B.
* La función debe verificar que el número de columnas de A sea igual al número de filas de B.
* Si no es así, la función debe retornar un mensaje indicando que la multiplicación no es posible.
* Si las dimensiones son correctas, la función debe calcular el producto matricial y devolver la matriz resultante.
```python
def multiplica_matrices(Lista_A, Lista_B):
    A = np.array(Lista_A)
    B = np.array(Lista_B)
    if A.shape[1] == B.shape[0]:
        resultado = np.dot(A, B)
        return resultado
    return "No se puede realizar la multiplicación de matrices"
```
Solución Básica
