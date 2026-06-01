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

