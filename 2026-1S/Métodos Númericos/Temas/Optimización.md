# Optimización
Recordandos los conceptos clásicos del cálculo diferencial, como los puntos críticos definidos por:
$$
f(c) = \text{max o min} \rightarrow f'(c) = 0  
$$
Es extremendamente util para procesos de ingeniería.
- Note que para poder realizar procesos de optimización, necesitamos lo que ya conociamos, métodos para encontrar raíces $(0)$ de la función y métodos para derivar una función
## Historial and Non-Computer
Contexto en la guerra y gran avance dependiendo del contexto.

#  1. Overview of One-Dimensional unconstrained Optimization
Goald: find the minimun or maximun of a single-function variable

## General Strategies for locating a Global Extremum
1. Graphical insight
2. Multiple Starting Guesses (random points)
3. Perturbation
# General Methods
- Bracketing Methods
    - Golden-Section Search
    - Parabolic Interpolation
- Open (Point) Methods (rely on derivatives):
    - Newton's method (solve f'(x) = 0 as a root-finding problem)
- Hybrid Methods:
    - Brent's Metho
# Golden-Section Searh Key Concepts
1. **Unimodal Interval** -- Assume [$xl$,$xu$]
2. **Interior Points** -- Choose
$$
d = \dfrac{\sqrt{5} - 1}{2} (x_u - x_l),\quad x_1 = x_l +d, \quad, x_2 = x_u - d
$$
3. **Interval Reduction** -- evaluate $f(x_1)$ and $f(x_2)$
* if $f(x_1) > f(x_2)$ (Seeking maximun, discard) $[x_l, x_2]$
* Otherwise, discard $[x_1, x_u]$
4. **Function- Evaluation Savings** - by reusing the interior point fron the previous iterarion, only one new evalyuation per step is needed.

>[!Example] 
Grafique directamente lo que esta realizando, eliminando el intervalo que siga siendo menor a la zona donde esta o se sospecha que debería estar el putno crítico, para descarta el intervalo solo debe utilizar un cambio de $x_u$ y $x_l$ dependiendo del caso
>- Use the golden-section search to find the maximun of
> $$f(x) = 2sin(x) - \dfrac{x^2}{10}$$
> withhin the interval $x_l = 0$ and $x_u = 4$
- Use el error relativo aproximado...

# Metodo Parabolic Interpolation
**Pupose:** Approximate the shape of a function f(x) near its extremum usin a quadratic (parabola).
**Key Idea:** Just as a straight line is uniquely defined by two pints, a parabola is uniquely defined by three points formula
$$
x_3 = \dfrac{f(x_0)(x_1^2-x_2^2) + f(x_1)(x_2^2-x_0^2) + f(x_2)(x_0^2-x_1^2)}{2[f(x_0)(x_1-x_2) + f(x_1)(x_2-x_0) + f(x_2)(x_0-x_1)]}
$$
x_3 = estimated extremum
>[!Example] 

>- Use the parabolic interpolation and Newton's Method to find the maximum of
> $$f(x) = 2sin(x) - \dfrac{x^2}{10}$$
> For Parabolic interpolation use an initial guesses of $x_0 = 0$, $x_1 = 1$, and $x_2 = 4$. For Newton's Method use an initial guess of $x_0 = 2.5$
- Use el error relativo aproximado...
Note que surge un conflicto, el condicional no es tan fácil de realizar

# Newton's Method for optimization
Backgrodun: Adaptation of newton-rapshon root-findgin to extrema of f(x)-
Resulta que ya no buscamos f(x), sino f'(x)

$$f'(x) = 0 \rightarrow  x_{i+1} = x_{i} - \dfrac{f'(x_i)}{f''(x_i)}$$
