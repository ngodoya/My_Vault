# Resumen
Se Analizan los metodos previamente analizados, ventajas, desventajas en el momento de codificar y ademas de tener que hacer un correcto analisis de los errores y un criterio dado.


Se introduce un nuevo tema:

# Matrices

> 1. Introducción

Ecuaciones algebraicas lineales
$$
\begin{cases}
a_{11}x + a_{12}y = b_1 \\
a_{21}x - a_{22}y = b_2
\end{cases}
$$
En sistemas $nxn$ donde $n\leq3$ se puede usar metodos a mano, pero en la vida real es complejo utilizar solo un metodo

## Notación Matricial

>[!Tip] Sería relevante recordar la notación matricial y como se manejaba en cursos previos, además de como transformar un sistema algebraico y verlo como una matriz nxn, finalmente recuerde los conceptos de los vectores y que para resolver un sistema con **n** incognitas necesitas **n** ecuaciones

$$
\left[ \begin{array}{cccc}
a_{11} & a_{12} & \cdots & a_{1n} \\
a_{21} & a_{22} & \cdots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{n1} & a_{n2} & \cdots & a_{nn}
\end{array} \right]
\left( \begin{array}{c}
x_1 \\
x_2 \\
\vdots \\
x_n
\end{array} \right)
=
\left( \begin{array}{c}
b_1 \\
b_2 \\
\vdots \\
b_n
\end{array} \right)
$$
### Matrices espaciales
- Simetricas
- Diagonales
- Identidad
- Superior y Inferior Triangular+

### Operaciones
- Suma, resta, multiplicacion escalar, multiplicación de matrices, transpuesta, traza, inversa.

## Organization

Como resolvemos estos sistemas??

### Gauss
el básico, se puede resumir como llevar una matriz de nxm a una matriz semejante de nxm pero con la caracteristica que es una matriz **Triangular Superior**.

### 1. Planos y rectas ($n\leq3$)

Con dos ecuaciones podemos visualizar todo esto como una recta
ejemplo, el sistema

$$
\begin{cases}
x + y = 1 \\
x + y = 2 
\end{cases}$$
puede hacer el despeje y visualizarlo en el plano cartesiano, el mismo metodo para R3 y tenemos una de las maravillas del algebra lineal, solo hay 3 casos 
>[!ERROR]
Note que es un método extremadamente delicado :(.
### 2. Regla de Cramer
Es bastante sencillo utilizar la regla de cramer, ya que solo necesita calcular determinantes.

$$
x_i = \dfrac{\text{Det([A] with column i replaced by {b})}}{Det([A])}
$$

>[!TIP]Máximo use matrices 3x3.

>[!IMPORTANT]
Lo bello de este metodo es que conociendo x_1 por ejemplo encontrar x_2 y x_3 se peude hacer con una sustición hacía atrás.

### 3. Eliminación de Incognitas

Sostiene el metodo de Gauss, es utilizar la idea del, escalar, sutraccion y eliminación.
>[!Example]
Use crammer's rule to solve

$$
\begin{cases}
0.3x+0.52y+z = -0.01 \\
0.5x +y + 1.9z = 0.67\\
0.1x + 0.3y + 0.5z = -0.44
\end{cases}
$$

un código excesivamente largo para resolver el método puede ser:
```python
import numpy as np
A = np.array([[0.3, 0.52, 1],[0.5, 1, 1.9],[0.1, 0.3, 0.5]])
b = np.array([[-0.01],[0.67],[-0.44]])

D = A[0,0] * (A[1, 1] * A[2, 2] - A[1, 2] * A[2, 1]) - A[0,1] * (A[1, 0] * A[2, 2] - A[1, 2] * A[2, 0]) + A[0,2] * (A[1, 0] * A[2, 1] - A[1, 1] * A[2, 0])

A_b1 = np.array([[-0.01, 0.52, 1],[0.67, 1, 1.9],[-0.44, 0.3, 0.5]])
D_1 = A_b1[0,0] * (A_b1[1, 1] * A_b1[2, 2] - A_b1[1, 2] * A_b1[2, 1]) - A_b1[0,1] * (A_b1[1, 0] * A_b1[2, 2] - A_b1[1, 2] * A_b1[2, 0]) + A_b1[0,2] * (A_b1[1, 0] * A_b1[2, 1] - A_b1[1, 1] * A_b1[2, 0])
x_1 = D_1 / D
print (x_1)

A_b2 = np.array([[0.3, -0.01, 1],[0.5, 0.67, 1.9],[0.1, -0.44, 0.5]])
D_2 = A_b2[0,0] * (A_b2[1, 1] * A_b2[2, 2] - A_b2[1, 2] * A_b2[2, 1]) - A_b2[0,1] * (A_b2[1, 0] * A_b2[2, 2] - A_b2[1, 2] * A_b2[2, 0]) + A_b2[0,2] * (A_b2[1, 0] * A_b2[2, 1] - A_b2[1, 1] * A_b2[2, 0])
x_2 = D_2 / D

print(x_2)
A_b3 = np.array([[0.3, 0.52, -0.01],[0.5, 1, 0.67],[0.1, 0.3, -0.44]])
D_3 = A_b3[0,0] * (A_b3[1, 1] * A_b3[2, 2] - A_b3[1, 2] * A_b3[2, 1]) - A_b3[0,1] * (A_b3[1, 0] * A_b3[2, 2] - A_b3[1, 2] * A_b3[2, 0]) + A_b3[0,2] * (A_b3[1, 0] * A_b3[2, 1] - A_b3[1, 1] * A_b3[2, 0])
x_3 = D_3 / D

print(x_3)
```
una alternativa excesivamente más sencilla puede ser:
```python
print(np.linalg.det(A_b1) / np.linalg.det(A))
```
# Na $\ddot{i}$ ve Gauss
## Dos fases
- Eliminación hacía adelante (para conseguir un sistema )

- Sustitución hacía atras para conocer lo desconocido

Diferencias con Gauss normal (no hacemos pivoteo, intercambio de filas)
### Back subtituon
1. Solve for the last unkown:
$$ x_n = \dfrac{b^{n-1}_n}{a_{nn}^{n-1}}$$
2. For i = n-1, n-2, ..., 1
$$x_n = b'_n / a'_{nn}$$
>[!Example]
Use Gauss elimination to solve

$$
\begin{cases}
3x-0.1y-0.2z = -7.85 \\
0.1x +7y - 0.3z = -19.3\\
0.3x - 0.2y + 10z = 71.4
\end{cases}
$$


>[!Tip] Note que para encontrar el multiplicador necesario por ejemplo plantea
$F_2 \rightarrow F_2 - mF_1$ m es simplemente $A_{21}/A_{11}$

# Gauss-Jrodan Method
Buscar una matriz identidad, solucion de cada incognita

> 2. Gauss elimination


> 3. Gauus Seidel
# Overview

> 4. Linear algebraic


