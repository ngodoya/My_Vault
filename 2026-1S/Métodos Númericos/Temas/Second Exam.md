# Optimization
You can check the official Presentation :D, click [HERE](Optimization.pdf)



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
2. 
## 3. Multidimensional Unconstrained Optimization

## 4. Constrained Optimization

## 5. Case Studies: Optimization

## 6. Summary
