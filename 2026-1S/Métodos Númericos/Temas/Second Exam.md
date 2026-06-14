[[# Optimization|Optimization]]
[[#Curve Fitting|Curve Ftting]]
# Optimization
You can check the official Presentation :D, click [[4. Optimization.pdf|Here]] 
## CONTENIDO

* **1.** [[#1. Introduction|Introduction]]
* **2.** [[#2. One-Dimensional Unconstrained Optimization|One-Dimensional Unconstrained Optimization]]
* **3.** [[#3. Multidimensional Unconstrained Optimization|Multidimensional Unconstrained Optimization]]
* **4.** [[#4. Constrained Optimization|Constrained Optimization]]
* **5.** [[#5. Case Studies Optimization|Case Studies: Optimization]]
* **6.** [[#6. Summary|Summary]]

---

## 1. Introduction
### Relationship to Root Finding
Optimization seeks the points where a function's derivative $f'(x)$ is equal to zero, you can use different criteria to determinate whether the critical point corresponds to a minimum or a maximum.
***Note:*** Remember the first and second derivative criteria:

| Derivative  | Function             | How?                                                                                                                                                                |
| ----------- | -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| $$f'(x)>0$$ | $$f(x)$$ *Increases* | We can know that a function has a maximum if, to the left of the critical point, the function is **increasing**, and to the right, it is **decreasing**.            |
| $$f'(x)<0$$ | $$f(x)$$ *Decreases* | Using the same reasoning, the function has a minimum if, to the left of the critical point, the function is **decreasing**, and to the right, it is **increasing.** |

| Derivative   | Function           | How?                                                                                                  |
| ------------ | ------------------ | ----------------------------------------------------------------------------------------------------- |
| $$f''(x)>0$$ | $$f(x)$$ *Convex*  | If the function is convex, the function is "smiling" :), which implies a local minimum                |
| $$f''(x)<0$$ | $$f(x)$$ *Concave* | If the function is concave, the function is sad :(, which implies a local maximum **(Forwing curve)** |

Many method reduce optimization to solving the root problem $f'(x)=0$, it's common use approximation for derivatives.
>[!useful]- Optimization in Engineering Practice
>- Unlike descriptive (simulation) models, optimization models are **prescriptive**, prescribing the best desing or course o action under physical and cost constraints.
### Classification of Optimization Problems

| By form of $f(x)$ ->                                     | By constraints ->                                 | By dimensionality                                 |
| -------------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- |
| - Linear Programming (linear f and constraint)           | Unsconstrained                                    | One-dimensional problem (single variable)         |
| - Quadratic programming (quadratic f, linear constraint) | Constrained (with equality/inequality conditions) | Multidimensional problems (two or more variables) |
| - Nonlinear programming (nonlinear f or constraints)     |                                                   |                                                   |
 
## 2. One-Dimensional Unconstrained Optimization
### Overview of One-Dimensional Unconstrained Optimization
- **Goal:** Find the minimum or maximum of a single-variable function (such as: $f(x), f(y), f(T)$...)
- **Challenges:** As we know, functions can be **multimodal**, meaning they may contain multiple local extrema; Distinguishing between local extrema and the **global** maximum is often nontrivial work.
### General Strategies for Locating a Global Extremum
1. **Graphical Insight** -- Visualize low-dimensional functions to identify likely global optima.
2. **Multiple Starting Guesses** -- run a local optimizer from a varied (possibly random) starting points and select the best result.
3. **Pertubation** -- after converging to a local extremum, slightly perturb the solution and rerun to check for better optima
### Classification of One-Dimensional Optimization Methods
- **Bracketing Methods** (require an initial interval $[x_l,x_u]$ containing a single extremum):
	- *Golden-section Search*
	- *Parabolic Interpolation* (faster convergence but risk of divergence)
- **Open (Point) Methods** (rely on derivatives):
	- *Newton's Method* (solve $f'(x)=0$ as a root-finding problem)
- **Hybrid Methods:**
	- *Brent's Method* (Combines Golden-seciton reliability with parabolic speed)
#### Golden-Section Search Key Concepts
1. **Unimodal Interval** -- assume $[x_l, x_u]$
2. **Interior Points** -- choose $$d = \dfrac{\sqrt{5}-1}{2}(x_u-x_l),\qquad x_1 = x_l + d, \qquad x_2 = x_u - d$$
3. **Interval Reduction** -- evaluate $f(x_1)$ and $f(x_2)$
	- If $f(x_1) >f(x_2)$ (seeking maximum), discard $[x_l,x_2]$.
	- Otherwise, discard $[x_1, x_u]$
4. **Function-Evaluation Savings** -- By reusing the interior point from the previous iteration, only one new evaluation per step is needed.

>[!Explain]- How it works?
>Imagine a unimodal function, that means the function only got a single maximum or minimum in the interval
>## For Maximum Case
>$$f(x_1)>f(x_2)$$
>with: $$x_l<x_2<x_1<x_u$$
>then the function is higher at $x_1$ than at $x_2$, and we know that the function is **unimodal**, the maximum could not be at the left of $x_2$, this explain why we are only using the interval $[x_1,x_u]$ (note that in other word we can say explain this as: $x_l = x_1$)
>- The main reason is, if we say that the maximum is on $[x_l,x_2]$ the function should be decreasing next after passing the maximum, that contradicts our initial supposition $f(x_1)>f(x_2)$
>### Notes
>This method don't know which point is closer to the maximum, only give the idea for closing the interval (and still knowing that the maximum is on that interval)

>[!Abstract] Criteria for stopping
>A nice Criteria for knowing of much iterations you will need would be $|f'(x)|<\epsilon_y$, but that means conflicts if you don't know the derivative of the funciton.

>[!Example]- Example 1
>Use the golden-section search to find the maximum of $$f(x)=2sin(x)-\dfrac{x^2}{10}$$
>within the interval $x_l=0$ and $x_u = 4$
># Golden Search
>Find the minimum of the following funciton in  interval $[0, 4]$ $$f(x)=x^2-6x+15$$

The method only discards intervals without knowing exactly where the optimum is.

**Video** [Here](https://www.youtube.com/watch?v=hLm8xfwWYPw)

![[Pasted image 20260607162222.png]]
![[Pasted image 20260607162105.png]]

### Parabolic Interpolation
- **Purpose:** Approximate the shape of a function f(x) near its extremum using a quadratic (parabola).
- **Key idea:** Just as a straight line uniquely defined by two points, a parabola is uniquely defined by three points.
- Formula:$$x_3 = \dfrac{f(x_0)(x_1^2-x_2^2) + f(x_1)(x_2^2-x_0^2) + f(x_2)(x_0^2-x_1^2)}{2[f(x_0)(x_1-x_2) + f(x_1)(x_2-x_0) + f(x_2)(x_0-x_1)]}$$
- Where $x_0, x_1, x_2$ are three guesses bracketing the optimum, and $x_3$ is the stimated extremum.
>[!Note]- Convergences
>Parabolic interpolation generally converges faster than the Golden-Section Search because it uses the function values at three points to approximate the local curvature of the objective function.
>	Unlike the Golden-Section Search, which only reduces the search interval, parabolic interpolation attempts to estimate the optimum directly by fitting a quadratic polynomial and computing its vertex.
>	The method can achieve significantly faster convergence near the optimum, but it is less robust and may fail when the fitted parabola poorly approximates the objective function.

### Brent Method
*"Use the fast method whenever it seems trustworthy; otherwise, fall back to the safe method."*
In this section we describe an algorithm which combines **golden section search** and **successive parabolic interpolation** 

| **Golden-Section Search**   | **Succesive Parabolic Interpolation** |
| --------------------------- | ------------------------------------- |
| Guaranteed Mnimum (Maximum) | Not Guaranteed                        |
| $$\alpha = 1$$              | $$\alpha = 1.325$$                    |
In this case $\alpha$ is used for talking about the convergence order
![[Pasted image 20260613171909.png]]
$Given:$
unimodal $f(x) [a, b]$
$v \leftarrow w \leftarrow x$
$a + \left(\dfrac{3-\sqrt5}{2}\right)(b-a)$
![[Pasted image 20260613172335.png]]
**SPI:** Sucessive Parabolic Interpolation
"Then $f$ is evaluated at the new point u, the points $a, b, v, w$ and $x$ are uptated as necessary, and the cycle is repeated"
$$x_{n+1}= x_n + \dfrac{1}{2}\left[\dfrac{(x_{n-1}-x_n)^2(y_n-y_{n-2})+(x_{n-2}-x_n)^2(y_{n-1}-y_n)}{(x_{n-1}-x_n)(y_n-y_{n-2})+(x_{n-2}-x_n)(y_{n-1}-y_n)}\right]$$
$$u = x + \frac{p}{q}$$

The main idea is avoid the case when $q \approx 0$, this happened when whatever points are the same, other common mistake from SPI method is: u is not always in $[a,b]$, if those case occurs the best idea would be switch to **GSS** $$u= \begin{cases}\dfrac{\sqrt5 - 1}{2}x + \dfrac{3-\sqrt 5}{2} a \quad \text{if }x \geq m \\ \dfrac{\sqrt5 - 1}{2}x + \dfrac{3-\sqrt 5}{2} b \quad \text{if }x \leq m \end{cases}$$
>[!Example]- Brent Method
>$$f(x) = \frac{x^3}{3} -\frac{x^2}{2} - x - 1 \quad \epsilon = 10^{-6} \quad [1, 2]$$ 
>**Note:** Usually the algorithm stops doing GSS steps, and eventually does only PSI


### Newton's Method for Optimization
- Background: Adaptation of Newton-Rapshon root-finding to extrema of f(x).
- Iteration Formula: $$x_{i+1}=x_i-\dfrac{f'(x_i)}{f''(x_i)}$$
- Characteristics:
	- Open method: Does not require initial bracketing of the optimum.
	- Rapid (quadratic) convergence when close to the solution.
	- Potential Divergence: if the initial guess is poor of if $f''(x_i)$ is zeros/changes sign. 
- Practical advice: Always check that the second derivative has the desired sign (positive for a minimum, negative for a maximum) to ensure convergence to the intended extremum.
>[!Example]- Example 2
>Use the parabolic interpolation and Newton's Method to find the maximum of $f(x) = 2sin(x) - \dfrac{x^2}{10}$
>FOr parabolic interpolation use an initial guesses of $x_0=0,x_1=1,x_4$, For Newton's Method use an initial guess of $x_0 = 2.5$


## 3. Multidimensional Unconstrained Optimization
### Overview: Multidimensional UNconstrained Optimization
- **Goal:** Find minima or maxima of functions of several variables.
- Focus here: Two-dimensional case (mountains and valleys analogy).
- Classification of methods:
	- Non-gradient (Direct) methods
	- Gradient (Descent/ascent) methods
### Direct Methods (Non-gradient)
#### Random Search
- Brute-force sampling of function at random points.
- In theory, random search can approach the global optimum as the number of samples tends to infinity.
- Drawbacks:
	- HIghly ineddificiente as dimensionality grows.
	- Ignores any information about function behavior
#### More sophisticated Heuristics
- Simulated annealing
- Tabu Search
- Artificial neural network
- **Genetic algorithms** most widely used; pioneered by Holland 1975; overviews by Davis 1991 and Goldberg 1989)


>[!Code]- Useful For Python
>if you want to generate a random interval (array), the best option would be
>```python
>x_range = np.random.uniform(-2, 2, n)
># np.argmax() useful for finding the index from maxima 
>```



>[!Tip]- Searching max or min
Random search evaluates the objective function at many randomly generated points and keeps the best solution found so far.

## 4. Constrained Optimization
- Deals with optimization problem where constraints play a role.
- When both the objective function and the constraints are linear, specialized methods (linear programming) can solve very large problems efficiently.
- Applicable in diverse engineering and management settings.
- Nonlineear constrained optimization is discussed more briefly, and software package options are surveyed
### Linear Programming (LP) Definition 
- An LP problem seeks to maximize (or minimize) a linear objective (e.g., profit or cost) subject to linear constraints representing limited resources.
- Linear” refers to the fact that both the objective and all constraints are linear functions of the decision variables.
- Programming” here means “scheduling” or “setting an agenda,” not computer programming
### Graphical Solution (for Two-Variable LPs)
- Plot each linear constraint as a straight line in the $x_1 - x_2$ plane
- (with 𝑥1 on the horizontal axis, 𝑥2 on the vertical axis). 
- The region where all constraints overlap (including 𝑥1 ≥ 0 and 𝑥2 ≥ 0) is the feasible solution space, containing all points that satisfy every constraint.
>[!Example] Example 4
>**Obtain a graphical solution to the following linear programming problem.**
>$$maximize \quad Z  = 150x_1 + 175x_2$$
>subject to
>$$7x_1+11x_2 \leq 77$$
>$$10x_1 + 8x_2 \leq 80$$
>$$0\leq x_1 \leq 9$$
>$$0 \leq x_2 \leq 6$$
## 5. Case Studies: Optimization

## 6. Summary
# Curve Fitting
You can check the official Presentation :D, click [[5. Curve Fitting.pdf]] 
## CONTENT 
[[#1. Introduction|1. Introduction]] 
[[#2. Least-Squares Regression|2. Least-Squares Regression]] 
[[#3. Interpolation|3. Interpolation]] 
[[#4. Fourier Approximation|4. Fourier Approximation]] 
[[#5. Curve Fitting with Software Packages|5. Curve Fitting with Software Packages]] 
[[#6. Summary|6. Summary]]
## 1. Introduction
### Motivation
* Useful for estimating intermediate values from discrete data.
* Two general approaches:
	* **Trend-Fitting** (noisy data -> least-squares regression)
	* **Interpolation** (precise data -> exact passage through points)
### Mathematical Background
**Simple Statistics**
- Arithmetic mean, variance, standar deviation, coefficient of variation
**The normal distribution**
- Histogram Approximation by bell-shaped curve
- Relation Between $\sigma, \mu$ and probability intervals
**Estimation of Confidence Intervals**
z- and t- distributions of two-sided intervals
### Methods
**Trade-offs**
Comparative Advantages and limitations of regression vs. interpolation
**Important Methods:** Key methods for regression, Interpolation, Fourier fits, confidence intervals
**Advanced Methods**
Matrix Formulations, general linear models, software-based implementations
## 2. Least-Squares Regression
### Motivation for Least-Squares Regression
- Experimental data often noisy; high-order interpolating polynomials oscillate and yield poor predictions between points.
- A simpler trend-fitting function capture the overall behavior without overfitting.
### Linear Model and Residuals
- Model $y = a_0 + a_1x + e$
- Residual (error) for each point $(x_i, y_i)$:$$e_i = y_i - (a_0+ a_1x_i)$$
**Closed-Form Solutions:**
Slope $$a_1 = \dfrac{n\sum x_i y_i -\sum x_i \sum y_i }{n\sum x_i^2 - (\sum x_i)^2}$$
Intercept $$a_0 = \bar y - a_1 \bar x$$
### Extension to Higher-Order Polynomials
Instead of fitting $$y = a_0 + a_1 x + e$$
we fit an mth-order polynomial $$y = a_0 + a_1x + a_2x^2 + \cdots + a_mx^m + e$$
### Extension to Higher-Order Polynomials
$$\begin{cases}(n)a_0 + \left(\sum{x_i}\right)a_1 + \left(\sum{x_i^2}\right)a_2 = \sum{y_i}\\ 
\left(\sum{x_i}\right)a_0 + \left(\sum{x_i^2}\right)a_1 + \left(\sum{x_i^3}\right)a_2 = \sum{x_iy_i}\\
\left(\sum{x_i^2}\right)a_0 + \left(\sum{x_i^3}\right)a_1 + \left(\sum{x_i^4}\right)a_2 = \sum{x_i^2y_i}\end{cases}$$
but also, in my case this is unpractical, the best idea it could be:
	**polynomial nth grade** $n=1$ $$\underset{m\times 2}{\begin{bmatrix}1 & x_1 \\\vdots & \vdots\\ 1 & x_m\end{bmatrix}}\underset{2\times 1}{\begin{bmatrix}c_0  \\ c_1 \end{bmatrix}} = \underset{m\times 1}{\begin{bmatrix}\text{All Observed Data}\end{bmatrix}} $$
	$nth$	
	$$\underset{m\times (n+1)}{\overset{x^0 \quad x^1 \qquad x^n}{\begin{bmatrix}1 & x_1 & \cdots & x_1^n \\\vdots & \vdots & \ddots & \vdots\\ 1 & x_m & \cdots & x_m^n\end{bmatrix}}}\underset{(n+1)\times 1}{\begin{bmatrix}c_0  \\ \vdots \\ c_n \end{bmatrix}} = \underset{m\times 1}{\begin{bmatrix}\text{All Observed Data}\end{bmatrix}} $$
Notice that m is the quantity of data that we got (point), and n is the polynomial grade
## 3. Interpolation
## 4. Fourier Approximation
## 5. Curve Fitting with Software Packages