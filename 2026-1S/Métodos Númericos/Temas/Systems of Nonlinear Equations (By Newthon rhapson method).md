$$

u_{i+1} = u_i + (x_{i+1}-x_i)\dfrac{\partial u_i}{\partial x} + (y_{i+1}-y_i)\dfrac{\partial u_i}{\partial y}
$$
$$
x_{i+1} = x_i - \dfrac{u_i\dfrac{\partial v_i}{\partial y}-v_i\dfrac{\partial u_i}{\partial y}}{\dfrac{\partial u_i}{\partial x}\dfrac{\partial v_i}{\partial y}- \dfrac{\partial u_i}{\partial y}\dfrac{\partial v_i}{\partial x}}
$$
$$
y_{i+1} = y_i - \dfrac{v_i\dfrac{\partial u_i}{\partial x}-u_i\dfrac{\partial v_i}{\partial x}}{\dfrac{\partial u_i}{\partial x}\dfrac{\partial v_i}{\partial y}- \dfrac{\partial u_i}{\partial y}\dfrac{\partial v_i}{\partial x}}
$$
> [!Example] Example 8
Use the multiequation Newton-Raphson method to determine roots of the equations. Note that a correct pair of roots is $x= 2$ and $y = 3$. Iniate the computation with guesses of $x_0 = 1.5$ and $y_0 = 3.5$.
$$u(x,y) = x^2 +xy - 10 =0 \quad and \quad v(x,y) = y+3xy^2-57=0$$

El metodo nos pide contrar las derivadas parciales de cada funcion con respecto a $x$ y $y$
***Resultando en:***
$$
u_x = 2x + y; \quad u_y = x; \quad v_x = 3y^2; \quad v_y = 1+6xy
$$
#### Ahora plantee sus iteraciones
> [!info]- Code 
> ```python
> x0 = 1.5
> y0 = 3.5
> # Funciones
> u = lambda x, y:  x**2 + x * y  - 10v = lambda x, y: y + 3 * x * y**2 - 57
> # Funciones derivadas
> u_x = lambda x, y: 2 * x + y
> u_y = lambda x, y: x
> v_x = lambda x, y: 3 * y**2 
> v_y = lambda x, y: 1 + 6 * x * y
> # Funciones derivadas
> u_x = lambda x, y: 2 * x + y
> u_y = lambda x, y: x
> v_x = lambda x, y: 3 * y**2 
> v_y = lambda x, y: 1 + 6 * x * y
> # Valores de x, y en el futuro
x_i = lambda x_0, y_0: x_0 - (u(x_0, y_0) * v_y(x_0, y_0) - v(x_0, y_0) * u_y(x_0, y_0)) / (u_x(x_0, y_0) * v_y(x_0, y_0) - u_y(x_0, y_0) * v_x(x_0, y_0))
y_i = lambda x_0, y_0: y_0 - (v(x_0, y_0) * u_x(x_0, y_0) - u(x_0, y_0) * v_x(x_0, y_0)) / (u_x(x_0, y_0) * v_y(x_0, y_0) - u_y(x_0, y_0) * v_x(x_0, y_0))
> ```


>[!check]- Iteraciones
>2.0360288230584467 3.052681086623569
2.0000819847658895 3.0005626461344974
1.9999999829118786 3.000000064843823
1.9999999999999998 3.000000000000001
2.0 3.0
2.0 3.0


## Conventional methods
#### Muller's Method
![[Pasted image 20260318150428.png]]![[Pasted image 20260318150647.png]]![[Pasted image 20260318150845.png]]
>[!example] Example 9
>Apply the  Mullers's Method using the starting estimatex $x_0 = 4.5$, x_1 = 5.5, and x_2 = 5.0 to locate one real solution of the cubic poylnomial $$f(x) = x^3-13x-12$$
>(For reference, the exact roots of this equiation are -3, -1 and 4) 

>[!IMPORTANT]
>$b \pm \sqrt{b^2+4ac}$ se escoger el que maximice el denominador en valor absoluto
># Porqué?

Ahora en el metodo se desplaza
$$x_1 -> x_0$$
$$x_2 -> x_1$$
$$x_3 -> x_2$$


