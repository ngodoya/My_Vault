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
## 3. Multidimensional Unconstrained Optimization

## 4. Constrained Optimization

## 5. Case Studies: Optimization

## 6. Summary
