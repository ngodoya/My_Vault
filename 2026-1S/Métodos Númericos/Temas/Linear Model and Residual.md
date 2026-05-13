Llegue tarde ;v
>[!abstract] Repaso
>- $$Model = y = a_0 + a_1x + e$$
>- Residual (errrir) for each point($x_i,y_i$):$e_i = y_i - (a_0 + a_1x_i)$
>- **Closed- Form Solutions**
>- *Slope* $$a_1 = \dfrac{n\sum x_iy_i - \sum x_i \sum y_i}{n \sum x_i^2 - (\sum x_i)^2}$$
>- *Intercept* $a_0 = \bar{y} - a_1 \bar{x}$

| $x_i$ | $y_i$ | $x_i^2$ | $x_i^3$ | $x_i^4$ | $x_i y_i$ | $x_i^2y_i$ |
| ----- | ----- | ------- | ------- | ------- | --------- | ---------- |
| 0     | 2.1   | 0       | 0       | 0       |           |            |
| 1     | 7.7   | 1       |         |         |           |            |
| 2     | 13.6  | 4       |         |         |           |            |
| 3     | 27.2  | 9       |         |         |           |            |
| 4     | 40.9  | 16      |         |         |           |            |
| 5     | 61.1  | 25      |         |         |           |            |
|       |       |         |         |         |           |            |
>[!Important]- Extension to Higher - Order Polynomials
>$$\begin{cases}
>(n)a_0 + \left(\sum x_i\right)a_1 + \left(\sum x_i^2\right)a_2 = \sum y_i \\
> 
>\end{cases}
>$$

## Interpolation
Función que pasa a traves de todos los datos ==(Puede intentar predecir un futuro)==, 2 puntos *(recta)*, 3 puntos *(parabola)* 
$$f(x) = a_0 + a_1x + a_2x^2 + a_nx^n$$
que pasa por los datos $n+1$
### Linear Interpolation (First-Order Case)
- The simplest interpolation connects two data point $(x_0, f(x_0))$ and $(x_1, f(x_1))$ with a straight line.
- From similar triangles: $$\dfrac{f_1(x)-f(x_0)}{x-x_0} = \dfrac{f(x_1)-f(x_0)}{x_1-x_0}$$
- Rearranged (linear-interpolation formula):$$f_1(x) = f(x_0)+\dfrac{(f(x_1)-f(x_0))(x-x_0)}{x_1-x_0}$$
>[!Example] Example 2
>Estimate the natural logarithm of 2 using linear interpolation. First, perfom the computation by interpolating between $ln(1) = 0$ and $ln(6) = 1.791759$. Then, repeat the procedure, but use a smaller interval from $ln(1)$ to $Ln(4) = 1.386294$. Note that the tur value of $Ln(2) = 0.6931472$

### Quadratic Interpolation (Three Points)
- ***Newton's Form:*** (Intente visualizarlo para una cubica (4 puntos))$$f_2(x) = b_0 + b_1(x-x_0)+b_2(x-x_0)(x-x_1)$$
- ***Coefficiente formulas:*** $$b_0 = f(x_0)$$
- $$b_1 = \dfrac{f(x_1)-f(x_0)}{x-x_0}$$
- $$b_2 = \dfrac{\dfrac{f(x_2)-f(x_1)}{x_2-x_1}-\dfrac{f(x_1)-f(x_0)}{x_1-x_0}}{x_2-x_0}$$
> [!Example] Example 3
> Fit a second-order polynomial to the following three points:
> $$x_0 = 1 \quad f(x_0) = 0$$
> $$x_1 = 4 \quad f(x_1) = 1.386294$$
> $$x_2 = 6 \quad f(x_2) = 1.791759$$
### General Newton's Divided-Difference Interpolating Polynomial
***Objective:*** Fit an nth-order polynomial through *n+1* points
**Polinomial form:** $f_n(x) = b_0 + b_1(x-x_0) + b_2(x-x_0)(x-x_1) + \dots + b_n(x-x_0)\dots(x_-x_{n-1})$
***Divided-difference coefficients:***
$$b_0 = f(x_0)$$
$$b_1 = f[x_1, x_0]$$
$$b_2 = f[x_2,x_1,x_0]$$
$$b_n = f[x_n,x_{n-1},\dots,]x_1,x_0$$
Where
$$f[x_i,x_j] = \dfrac{f(x_i)-f(x_j)}{x_i-x_j}$$
$$f[x_i,x_j,x_k] = \dfrac{f[x_i,x_j]-f[x_j,x_i]}{x_i-x_j}$$
$$f[x_n,x_{n-1},\dots,x_1,x_0] = \dfrac{f[x_n,x_{n-1},\dots,x_1]-f[x_{n-1},x_{n-2},\dots,x_0]}{x_n-x_0}$$
>[!Example] Example 4
>In Example 3, same data, now, adding a fourth point, $[x_3 = 5; f(x_3) = 1.609438]$, estimate $Ln 2$ with a third- order Newton's interpolating polynomial

This is so boring, as you watched this method is so complex que you got $n+1$ points, but we can get a solution with a new method
## Lagrange Interpolating Polynomial
- **Definition:** A reformulation of Newton's polynomial that avoids computing divided differences.
- **General form:** $$f_n(x)=\sum_{i=0}^nL_i(x)f(x_i)$$
- **Basis polynomials $L_i(x)$**: $$L_i(x)=\prod_{j=0}^n\frac{x-x_j}{x_i-x_j} \quad; j\neq i$$
>[!Example]- Example 5
>Use a Lagrange interpolating polynomial of the first and second order to evaluate In 2 based on the following data:
>$$x_0 = 0\quad f(x_0) = 0$$
>$$x_1 = 4\quad f(x_1) = ln(4)$$
>$$x_2 = 6\quad f(x_2) = ln(6)$$

## Fourier Approximation
A systematic framework for representing arbitrary waveforms using trigonometric (sine/cosine) series.
### Periodic Functions
Definition: $f(t)$ is periodic if $$f(t) = f(t+T)$$
Where $T$ is the (smallest) period.
### Sinusoidal Model
General form: $$f(t) = A_0 + C_1cos(\omega_0t+\theta)$$
Parameters:
$A_0:$ mean (DC) value
$C_1:$ amplitude
$w_0:$ how much does repeat
### Least - Squares Fit of a Single Single Sinusoid
Model:$$y_i = A_0 + A_1cos(\omega_0t_i) + B_0cos(\omega_0t_i) +e_i$$
Normal Equations (Matrix Form)
$$\begin{bmatrix}
N & \sum cos(\omega_0 t) & \sum sin(\omega_0 t) \\
N & \sum cos^2(\omega_0 t) & \sum cos(\omega_0 t)sin(\omega_0 t) \\
N & \sum sin(\omega_0 t)cos(\omega_0 t) & \sum sin^2(\omega_0 t) 
\end{bmatrix} \begin{Bmatrix}A_0 \\ A_1 \\ A_2\end{Bmatrix} = \begin{Bmatrix}\sum y \\ \sum y cos(\omega_ot) \\ \sum y sin (w\omega_ot)\end{Bmatrix}$$
>[!Example]- Example 6
>The sinusoid curve is described by $y=1.7+cos(4.189t + 1.0472)$. Generate 10 discrete values for this curve at intervalts of $\Delta t = 0.15$ for the range $t=0$ to 1.35. Use this information to evaluate the coefficientes of by a least squares fit
>

# Excel zzzz
You are asked to fit the given data series (pairs of x and y values) to the logarithmic model $$y = a_0 +_1log(x)$$
Using Excel's Trendline too, in order to determine the coefficients $a_0$ and $a_1$ that best match the provided points.
>[!example] Example 8
>Generate a set of data point by sampling the function: $$f(x) = sin(x)$$
>at equally spaced xx-values from 0 to 10 with a step size of 1. then, using MATLAB, fit the resulting data {(x,y)} by means of:
>1. Linear interpolation
>2. A fifth-order polynomial
>3. A cubic spline
>Finally, comapre each fitted curve to the original sine data by evaluating and potting them on a finer x-grid (for example, with step size 0.25) over the interval [0, 10].

