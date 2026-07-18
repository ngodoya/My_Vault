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

# Operaciones Entre Matrices

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
