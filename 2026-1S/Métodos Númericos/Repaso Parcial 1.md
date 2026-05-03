# Formulas
#Errores 
- **True Error:** $Value_{real} - Approximation_{Value}$
- **Error Relativo Absoluto $\epsilon_t$:** $\dfrac{Value_{real} - Approximation_{Value}}{Value_{real}}$
- **Approximate Relative Error $\epsilon_a$:** $\dfrac{Current_{Approximation} - Previous_{Approximation}}{Current_{Approximation}}$
- **Taylor Series:** $f(x) = \sum\limits_{k=0}^{n} \dfrac{f^{(k)}(a)(x-a)^k}{k!}$
>[!Tip]- Series de Taylor y relación $h^{n+1}$
> El error es proporcional a: $h^{n+1}$ (En las series de Taylor)
> Es útil, para terminar el código poner una condición de $$\epsilon_a \leq \epsilon_s$$ donde $\epsilon_s$ es el porcentaje de error relativo deseado.


---
## Roots
#Raíces
There are so many methos for solving the roots in a equation, the first of them would be the bracketing Methods
### Bracketing Methods (Métodos de intervalo)
>[!Abstract] Useful Idea for error
>We need to see change in x, we can't compare it to the absolute 0 in the function, usually we try to use two conditions that will be.
>$f(x)<\epsilon_y$ and $\|x_{l}-x_{u}\|<\epsilon_x$
> where $\epsilon_y$ would be a factor as $10^{-3}$ or $10^{-6}$ same idea for $\epsilon_x$
> > See that $f(x_{l})\times f(x_{u})<0$ those values need to be from different sign.

Requires two initial *guesses*, ($x_l$ and $x_u$) you can find them using **graphical methods** *(those methods are useful for find values that you can use in bisection methods)*.
#### Bisection Method
in a interval continuous $[x_l, x_u]$ we can search a new point, that can be the root that we want, $$x_r = \dfrac{(x_u+x_l)}{2}\quad then\quad x_u = x_r \quad \text{if }f(x_u)\cdot f(x_r)\geq 0 \quad \text{in other case } x_l = x_r$$
>[!Error]- True error vs. approximate error behavior
>• True error εt may not decrease monotonically with each iteration.
>- However, the interval width Δxi containing the root is halved every iteration, ensuring predictable error
reduction.

### The False-Position Method (Linear interpolation method)
$$x_r = \dfrac{x_l\cdot f(x_u) - x_u\cdot f(x_l)}{f(x_u)-f(x_l)}$$
Use a line and uses its intersection, and the new conditions are the same as **bisection method**, in this case the corvengence is better than bisection method.***The deduction for this formula uses trigonometry***
- Problems if the function is so curve.
- don't use $\epsilon_x \geq |x_l-x_u|$ is better $\epsilon_x \geq |x_r{new}-x_r{old}|$

### Open Methods
- Open methods rely on a formula that uses one or two initial guesses and do not require enclosing the root.
- Open methods can sometimes diverge (moveaway from the true root), although when they converge they often do so more rapidly than bracketing methods.
#### Simple Fixed-Point Iteration
$$f(x) = 0 \xrightarrow{sumar \quad x} g(x) = x$$
$$x_{i+1} =g(x_i)$$
#### Two-Curve (Graphical) Method
Rewrite $x = g(x)$  as two curves
$$y_1 = x \quad y_2 = g(x)$$
 The roots of $f(x) = 0$ correspond to the intersections of these curves.
#### The Newton Raphson Method (GOAT)

$$x_{i+1} =x_i - \dfrac{f(x_i)}{f'(x_i)}$$
• *Inflection near root:* If $f′′ (x)= 0$ close to the root, successive iterates may diverge.
• **Oscillation:** The method can oscillate around a local maximum or minimum, sometimes settling at a slope near zero rather than the true root.
• **Jumping between roots**: An initial guess near one root can leap to another root farther away
+ **Max** if $f'(x) = 0$ will never converge
Need the derivative of the function (would be useful if you use a numerical derivative)

#### Secant Method
$$x_{i+1}=x_i - \dfrac{f(x_i)(x_i-x_{i-1})}{f(x_i)-f(x_{i-1})}$$
Don't need to use derivative, useful when $f'(x)$ is complex to find or costly to compute, substitue in newton raphson method using  **backward finite-differences**
>[!note] Notice that we need two guesses
>$x_{i-1}$ and$x_i$

#### Pitfalls from bracketing methods
Look at this example $$x(x-1)^2=0$$ we would think that is a good idea try to find the root using for example false position method, the problem is the graph, in x = 1, the curve is tangent and never cross the x axis :(, there is no and interval that $x_u$ and $x_l$ have different signs.
generalize for $m = 2n$, there is no problem when $m = 2n + 1$.
>[!Error]- Kill
>Open Methods lose with maximun (derivative = 0)
>Bracketing Methods lose with: No sign change

### Solution
#### Multilicity independent newton-raphson via u(x)
1. Define
$$u(x) = \dfrac{f(x)}{f'(x)}$$
2. Then $$x_{i+1} = x_i - \dfrac{u(x)}{u'(x)}$$
with
$$u'(x)= \dfrac{f'(x)^2-f(x)f''(x)}{f'(x)^2}$$
 Simplified iteration formula
 $$x_{i+1} = x_i - \dfrac{f'(x_i)f(x_i)}{f'(x_i)^2-f(x_i)f''(x_i)}$$
---
## Systems of Nonlinear Equations

>[!Example]- Example:
>$$\begin{cases}
>u(x, y) = x^2 + xy - 10 = 0 \\
>v(x, y) = y + 3xy^2 - 57 = 0
>\end{cases}
>$$

- Use a first-order multivariable Taylor series for each function:
$$
u_{i+1} = u_i + (x_{i+1}-x_i)\dfrac{\partial u_i}{\partial x} + (y_{i+1}-y_i)\dfrac{\partial u_i}{\partial y}$$
* Setting $u_{i+1} = v_{i+1} = 0$ yields two linear equations for $x_{i+1} and y_{i+1}$
* Solving via Cramer’s rule gives the update formulas:
$$x_{i+1} = x_i - \dfrac{u_i\dfrac{\partial v_i}{\partial y}-v_i\dfrac{\partial u_i}{\partial y}}{\dfrac{\partial u_i}{\partial x}\dfrac{\partial v_i}{\partial y}- \dfrac{\partial u_i}{\partial y}\dfrac{\partial v_i}{\partial x}}$$
$$y_{i+1} = y_i - \dfrac{v_i\dfrac{\partial u_i}{\partial x}-u_i\dfrac{\partial v_i}{\partial x}}{\dfrac{\partial u_i}{\partial x}\dfrac{\partial v_i}{\partial y}- \dfrac{\partial u_i}{\partial y}\dfrac{\partial v_i}{\partial x}}$$

### Muller Method
Nice method for finding complex roots, fits a parabola through three points stimation
##### Parabolic Model
define the interpolating parabola as: $$f(x) = a(x-x_2)^2 + b(x-x_2) + c$$
and the parabola must satisfie values on $f(x_0)$, $f(x_1)$, $f(x_2)$, if you evaluate in "$x_2$" you will obtain $c = f(x_2)$, substitute the identity in $f(x_0)$ and $f(x_1)$, giving you the next equations
$$\begin{cases}
f(x_0) - f(x_2) = a(x_0-x_2)^2 + b(x_0-x_2)
\\
f(x_1) - f(x_2) = a(x_1-x_2)^2 + b(x_1-x_2)
\end{cases}
$$
#### Finite differences notation
#finite_differences
$$h_0 = x_1 - x_0 \qquad h_1 = x_2 - x_1$$
$$\delta_0 = \dfrac{f(x_1)-f(x_0)}{x_1 - x_0} \qquad \delta_1 = \dfrac{f(x_2)-f(x_1)}{x_2 - x_1}$$
 you will obtain the value of b, clearing it $b = ah_1 + \delta_1$ , similar idea with a **(tricky point)**, final answer for muller:

$$\begin{cases}
c = f(x_2)\\
b = ah_1 + \delta_1\\
a = \dfrac{\delta_1 - \delta_0}{h_1 + h_0}

\end{cases}$$
likewise???
**Bhaskara**
$$x_3 = x_2 + \dfrac{-2c}{b\pm\sqrt{b^2-4ac}}$$
Choose the sign in the denominator that matches the sign of b, to maximize the
denominator and yield the estimate closest to x2​.
**Strategy 1 (Real roots only)**: Keep the two points nearest to the new estimate x3​.
**Strategy 2 (Real and complex roots)**: Shift points so that (x1, x2, x3​) replace (x0, x1, x2​)
for the next cycle.



 Tags: #Errores #finite_differences #Raíces
