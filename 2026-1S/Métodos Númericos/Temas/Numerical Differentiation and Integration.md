Repasando los conceptos clásicos del cálculo integral e diferencial, podemos utilizar métodos numéricos para solucionar solucionar integrales que no son tan sencillas de evaluar o integrar, recuerde librearas como ``scipy``

| Sección | Tema Principal                        | Descripción                                                                     |
| ------- | ------------------------------------- | ------------------------------------------------------------------------------- |
| **1.**  | **Introduction**                      | Conceptos básicos y fundamentos del análisis numérico.                          |
| **2.**  | **Newton-Cotes Integration Formulas** | Métodos cerrados y abiertos para el cálculo de integrales definidas (\(f(x)\)). |
| **3.**  | **Numerical Differentiation**         | Aproximación de derivadas usando diferencias finitas.                           |
| **4.**  | **Summary**                           | Repaso rápido de las fórmulas, errores y aplicaciones clave.                    |


## Overview
Summary about the previous subjects in engineer.
### Differentiation
- The first derivative gives the rate of change ($\dfrac{dy}{dx}$).
- The second derivative measures curvature.
- Partial derivatives describe slope on multivariable surfaces.
### Integration
- The inverse of differentiation: $\int_a^bf(x)$ represents area under the curve.
- Evaluating an integral is equivalent to solving $\dfrac{dy}{dx} = f(x)$ with and initial condition
---
#### Derivative-Integral Duality
- Differentiate position -> velocity; integrate velocity -> position.
- Both processes are complementary and framed as differential equations.
### Function Types in Numerical Work
- Simple continuous 8e.g., polynomials).
- Complex continuous (hard to treat analytically).
- Tabulated data (common in experiments).
---
#### Key Numerical Techniques
- Finite differences for derivatives.
- Quadrature formulas (redifined strip methods) for integrals.
- Curve-fitting plus differentiation for noisy data.
#### Engineering Applications
- Newton's law ($F = ma$)
## Newton-Cotes Strategy
Replace $f(x)$ over $[a, b]$ by a polynomial $f_n(x) = a_0 +a_1x+\cdots+a_nx^n$ , then integrate the polynomial instead of the original function.
### Closed vs. open forms
- Closed: use data at both endpoints a and b
- OPpen: integration limits extend beyond the data limits
# Trapezoidal Rule
**Single-segment Trapezoidal Rule**
$$I = \int_a^bf(x)dx \approx (b-a)\dfrac{f(b)+f(a)}{2}$$

**Composite (multiple-application) Trapezoidal Rule**
- Divide $[a,b]$ into n equal subinterval of width $h= \dfrac{b-a}{n}$
- Approximate each with the trapezoidal rule and sum:
$$I \approx \frac{h}{2}\left[f(x_0)+2\sum_{i=1}^{n-1}f(x_i)+f(x_n)\right]$$
>[!example]- Example 1
>Use the two-segment trapezoidal rule to estimate the integral of $$f(x) = 0.2+25x-200x^2+675x^3-900x^4+400x^5$$
>from a= 0 to b= 0.8. recall that the correct value fort the integral is 1.640533.

# Simpson's Rule
## Idea of Simpson's rules
Use higher-order interpolating polynomials (parabolas, cubics) through equally spaced points to approximate $$\int_a^b f(x)dx$$
## Simpson's 1/3 Rule (single segment)
- Divide $[a, b]$ at midpoint $x_1 = \frac{(a+b)}{2}$, with  $h=\frac{b-a}{2}$
- Formula:
$$I = \dfrac{h}{3}[f(x_0)+4f(x_1)+f(x_2)]$$
$$\frac{b-a}{6}\left[f(a)+4f\left(\frac{a+b}{2}\right)+f(b)\right]$$
**Composite Simpson's 1/2 Rule**
- Split $[a,b]$ into n even numbered subintervarls of widht h = (b-a)/n.
- Apply 1/3 rule on each adjacent pair and sum:
$$\approx\dfrac{h}{3}\left[f(x_0)+4\sum_{\text{i odd}}f(x_i)+ 2 \sum_{\text{j pair}}f(x_j) + f(x_n)\right]$$
### Simpson's 3/8 Rule (single segment)
Use four points $x_0$, $a$, $x_1=a+h$ , $x_2 = a+2h$, $x_3 = b$ with $h= (b-a)/3$
Formula:$$I \approx \dfrac{3h}{8}[f(x_0)+3f(x_1)+3f(x_2)+f(x_3)]$$
Slightly more acurrate than single 1/3 rule but requires and odd number of segments.
#### Combining 1/3 and 3/8
For an overall odd number of segments: apply $1/3$ rule on al but the last three, and $3/8$ rule on the final three to maintain thrid-order accuracy.
>[!Example]- Example 3
>Use simpson's 3/8 rule to integrate the previous function
>Use it in conjuction with simpson's 1/3 rule to integrate the same function for five segments.

# 3. Numerical Differentiation
Euler Method (Finite Differences)
## High-accuracy Differentiation Formulas
**What are these Formulas for?**
When you know the value of a function $f(x)$ only at equally spaced points $x_i$,$x_{i\pm1}$,$x_{i\pm2}$... (spacing h), yo ucan approximate its derivatives by replacing Taylor-series terms with finite-difference quotients.
- The **"short" formulas** use the minimum number of points and keep only the leading term
- the include additional taylor terms and combine several useful
### Three families schemes
| **Family**   | **Where it samples $f$**             | **Typical use** |
| ------------ | ------------------------------------ | --------------- |
| **Forward**  | $$x_i,x_{i+1}$$                      |                 |
| **Backward** | $$x_i,x_{i-1}$$                      |                 |
| **Centered** | Symetrically $$x_{i\pm1},x_{i\pm2}$$ |                 |
[Diapositivas](https://classroom.google.com/w/NzkzNjgwMDI3NzI4/t/all)

![[Pasted image 20260527142757.png]]
>[!Example]- Example 4
>Estimated the derivative of at $x = 0.5$ using finite divided differences and a step size
of $h = 0.25$: $$f(x) = -0.1x^4-0.15x^3-0.5x^2-0.25x+12$$

## Derivatives of Unequally Spaced Data
### Lagrange Interpolating Polynomial
Fit a second-order Lagrange polynomial to any three adjacent points (no equal spacing required) and differentiate it analytically.
### Resulting Expression (Three-Point Formula)
$$f'(x) = f(x_{i-1})\dfrac{x_i-x_{i+1}}{(x_{i-1}-x_i)(x_{i-1}-x_{i+1})}+f(x_i)\dfrac{2x_i-x_{i-1}-x_{i+1}}{(x_{i}-x_{i-1})(x_{i}-x_{i+1})} + f(x_{i+1})\dfrac{x_{i}-x_{i-1}}{(x_{i+1}-x_{i-1})(x_{i+1}-x_{i})}$$
![[Pasted image 20260527150516.png]]
