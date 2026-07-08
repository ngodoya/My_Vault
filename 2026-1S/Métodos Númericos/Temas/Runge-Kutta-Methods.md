# Euler Method (RK1)
You know of to use this, we will use the approximation from the slope using the derivative that we know
>[!Example] Example 1
>Use Euler's method to numerically integrate $$\dfrac{dy}{dx} = -2x^3+12x^2-20x+8.5$$
>from x=0 to x=4 with a step size of 0.5, The initial condition is x=0 is y=1 $$y(0)=1$$

## Limitations of Euler's Method
**Main Drawback:** assumes the slope $f(x_i,y_i)$ at the start of each step represent the entire interval, producing large local- truncation erros.
**Remedy:** evaluate the slope at additional points within the step and combine the stopes-- this idea leads to predictor-corrector-type improvements and, in the general case, to **Runge--Kutta (RK) methods.**
## Heun's (Improved Euler) Method
| **Step**            | **Formula**                     | **Description**                        |
| ------------------- | ------------------------------- | -------------------------------------- |
| **Predictor**       | $y_{i+1}^0=y_i+f(x_i,y_i)h$     | Euler estimate at the end of the step. |
| **End-point slope** | $y'_{i+1}=f(x_{i+1},y_{i+1}^0)$ | Slope using the predictor value        |
| **Average Slope**   | $y=\dfrac{y'_{i}+y_{i+1}'}{2}h$ |                                        |
>[!Example] Example 2
>Use Heun's Method to integrate $y' =4e^{0.8x}-0.5y$ from $[0, 4]$ with a step size of 1. The initial condition is $$y(0)=2$$

# Auxiliary (Boundary) Conditions in ODEs
- Ordinary differential equations (ODEs) always require additional conditions to determine the constants of integration.

- For an nth-order ODE, exactly n conditions are needed.

- When all conditions are specified at the same value of the independent variable, the problem is an initial-value problem (IVP).

- When the conditions are specified at different values—typically at the domain’s extremities—the problem is a boundary-value problem (BVP).
![[Pasted image 20260708143907.png]]
## Numerical Solution Strategies

Convert the BVP into an equivalent IVP by guessing the unknown initial slope (or value).

Integrate the IVP (e.g., with fourth-order Runge–Kutta) to the opposite boundary.

Compare the calculated end value with the prescribed boundary condition.

Iterate on the guess using a root-finding technique (secant, Newton, etc.) until the mismatch is acceptably small.

Non-linear two-point problems: A single linear interpolation between two “shots” may not converge; a quadratic fit of three shots often improves convergence, but root-finding frameworks are more robust.
### Finite-Difference Method (FDM)
1. Discretize the rod into $\mathbf{N}$ equally spaced node, $\Delta x = \dfrac{L}{N-1}$
2. Replace second  derivatives by their central finite-difference form:
$$\dfrac{d^2T}{dx^2}=\dfrac{T_{i+1}-2T_i+T_{i-1}}{\Delta x^2}$$
3. The interior node equations form a tridiagonal linear system, solvabel efficently via the #Thomas-algorithm or sparse solvers.

>[!Example]- Example 4
>Use the finite- difference  method to solve  the equation for a 10-m  rod with $h' =0.01m^21$, $T_a=20$, and the boundary conditions. With a segment lenght of $\Delta x=2m$
>$$\dfrac{d^2T}{dx^2}+h'(T_a-T)=0$$
>$$T(0)= 40, \quad T(10)= 200$$

Despejando y aplicando:
$$T_{i+1}-2T_i+T_{i-1} + \Delta x^2 h (T_a-T_{i})= 0$$
$$T_{i+1}=2T_i-T_{i-1} - \Delta x^2 h (T_a-T_{i})$$
Reorganizando terminos
$$T_{i+1}-T_{i}(2+\Delta x^2 h) + T_{i-1}=-\Delta x^2 hT_a$$
Start the iterations for First Node $i = 1$
$$T_{2} - T_{1}(2+\Delta  x^2 h) + 40 = -0.8$$
$i = 2$
$$T_{3} - T_{2}(2+\Delta  x^2 h) + T_1 = -0.8$$
$i = 3$

$$T_{4} - T_{3}(2+\Delta  x^2 h) + T_2 = -0.8$$
$$200 - T_{4}(2+\Delta  x^2 h) + T_{3} = -0.8$$



Tags: #Thomas-algorithm 
