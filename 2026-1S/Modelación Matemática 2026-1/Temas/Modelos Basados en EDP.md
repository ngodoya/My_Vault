# Clasificación de las #EDP
Después de usar el método de cramer donde plantemos una matriz 
$$
A = \begin{pmatrix}a_{11} & a_{12} & a_{13}\\
a_{21} & a_{22} & a_{23} \\
a_{31} & a_{32} & a_{33}
\end{pmatrix} \quad y = \begin{pmatrix} a \\ b \\ c
\end{pmatrix}
$$
donde podemos aplicar cramer en la ecuación dada como
$$
A\vec x = y ; \vec x = (x_1, x_2, x_3)^T
$$
$$
x_1 = \dfrac{M_1}{\det(A)};\quad M_1 = \begin{pmatrix}a & a_{12} & a_{13}\\
b & a_{22} & a_{23} \\
c & a_{32} & a_{33}
\end{pmatrix}$$
$$
A(y')^2+By'+C =  0
$$
Resultando en los casos según el discriminante $\sqrt{B^2-4AC}$
* $B^2-4AC > 0$ Dos curvas resultantes ***Hiperbolica***
* $B^2-4AC = 0$ Una resultante ***Parabólica***
*  $B^2-4AC < 0$ Complejos ***Eliptica*** 
--- 
## Trabajemos con una EDP Hiperbolica

>[!Example]
>$$\dfrac{\partial ^2 f}{\partial t^2} = c^2\dfrac{\partial ^2 f}{\partial x^2} \longrightarrow \dfrac{\partial ^2 f}{\partial t^2} - c^2\dfrac{\partial ^2 f}{\partial x^2}= 0$$
>$A = 1$
>$B = 0$
>$C = -c^2$
>Cómo analizariamos que tipo de curva es?
>Tiene sentido que sea una **Hiperbolica**?

## Trabajemos con una EDP Parabólica

>[!Example]
>$$\dfrac{\partial  f}{\partial t} = k\dfrac{\partial ^2 f}{\partial x^2} \longrightarrow \dfrac{\partial f}{\partial t} - k\dfrac{\partial ^2 f}{\partial x^2}= 0$$
>$A = k$
>$B = 0$ ¿Hay derivadas ***Cruzadas***?
>$C = 0$ ¿Hay otra derivada  de segundo orden?
>Cómo analizariamos que tipo de curva es?
>Tiene sentido que sea una **Parabólica**?

* Definen Problemas de ***Valores en la Frontera*** #Valor_Frontera 
* No podemos corregir el pasado con el futuro, no hay forma de que podamos afectar el pasado, SI O SI curva característica una recta 
## Trabajemos con una EDP Elíptica

>[!Example]
>$$\dfrac{\partial ^2 f}{\partial x^2} + \dfrac{\partial ^2 f}{\partial xy^2}= g $$
>$A = 1$
>$B = 0$ ¿Hay derivadas ***Cruzadas***?
>$C = 1$ ¿Hay otra derivada  de segundo orden?
>Cómo analizariamos que tipo de curva es?
>Tiene sentido que sea una **Parabólica**?
* Propiedades de los difusivo
--- 
# Ejercicio Para la Casa!!!
- Busque en diapositivas

### Condiciones de Frontera

1. Dirichlet (D): $f = a$ ***Define*** el valor de la variable, Ej : $T_{\gamma_1}=300k(sin\omega t)$ ***¡¡SIGUE SIENDO CONDICIÓN DE FRONTERA!!***
2. Neumann (N): $\dfrac{\partial f}{\partial n} = a$ ,$n?$ este muchacho **Define** la dirección ***normal*** respecto a nuestra frontera Ej: $\dfrac{\partial T}{\partial x} = b$
		 Condición especial: Adiábatico (Frontera Adiábatico)
3.  Fourier (R) o Robin: $\alpha f + \beta \dfrac{\partial f}{\partial n} = a$ Ej: $\alpha T + \beta \dfrac{\partial T}{\partial y} = a$ en un $\gamma_3$ $n=y$ porque y es perpendicular a la frontera
		1. Note que las dimensiones de $\alpha \beta$ no son iguales, en el caso ideal $[\beta] = 1$ y $\alpha = ???$ pues con análisis dimensional note que  las unidades del segundo termino son $\left[\dfrac{\partial f}{\partial y}\right] = \dfrac{\theta}{L}$ esto implica que $\alpha = L^{-1}$
4.  Cauchy (C): $f = a \quad Y \quad \dfrac{\partial f}{\partial n} = b$

Fronteras dadas como $\gamma$ :
* 1D Puntos (recta)
* 2D Segmentos de Curvas
* 3D Cascarones
# Qué hablamos en las #EDP
* Dominio $\Omega$
* Fronteras
>[!note] 1D
>$x \in [a, b]$
>---
>Fronteras a y b
>>[!note] 2D
>>$x \in x^2+y^2 < 1$
>>---
>>#Frontera sería la circunferencía
>>$x^2+y^2 = 1$

Tags: #EDP #Frontera #Valor_Frontera #Frontera