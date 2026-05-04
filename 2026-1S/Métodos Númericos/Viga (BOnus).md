## Análisis de Deflexión de una Viga en Voladizo

Una viga en voladizo (cantiléver) de longitud $L$ está sujeta a una carga constante $w$ (fuerza por unidad de longitud). El desplazamiento vertical $y$ en un punto situado a una distancia $x$ del extremo empotrado se puede calcular mediante la relación de forma cerrada:

$$y(x) = \frac{w}{24EI} (x^4 - 4Lx^3 + 6L^2x^2)$$



### Parámetros del Sistema
* **Módulo elástico ($E$):** $2 \times 10^{11} \text{ Pa}$
* **Segundo momento de área ($I$):** $3.3 \times 10^{-4} \text{ m}^4$
* **Intensidad de carga uniforme ($w$):** $12000 \text{ N/m}$
* **Longitud total de la viga ($L$):** $4 \text{ m}$

### Pendiente de la Curva
Si se diferencia con respecto a $x$, la pendiente de la curva de deflexión resulta:

$$\frac{dy}{dx} = \frac{w}{24EI} (4x^3 - 12Lx^2 + 12L^2x)$$

### Tarea de Implementación
Asumiendo que la deflexión en el soporte es cero, $y(0) = 0$, implemente el **Método de Euler hacia adelante** con un tamaño de paso $\Delta x = 0.125 \text{ m}$ para avanzar desde $x = 0$ hasta $x = L$. 

Calcule la secuencia de deflexiones aproximadas y grafique estos valores numéricos junto con el perfil exacto proporcionado por la fórmula anterior.
>[!Check]- Solución
>```python
>#Definición Constante
>E = 2e11
>I = 3.3e-4
>w = 1.2e4
>L = 4.0
>#Todas las unidades estan en la dimension encesaria
>derivative = lambda x: w * (4 * x **3 - 12 * L * x**2 + 12 * L**2 * x) / (24 * E * I)
>real_sol =  lambda x: w * (x **4 - 4 * L * x**3 + 6 * L**2 * x**2) / (24 * E * I)
>Creamos un vector de x
>x0 = 0.0
>xf = 4.0
>dx = 0.125
>vect_x = np.arange(x0, xf + dx, dx)
># Creamos vector solución con condicion inicial
>y_sol_num = np.zeros(len(vect_x))
>y_sol_num[0] = 0.0
>y_sol_an = real_sol(vect_x)
>#Implementamos euler hacía adelante
>for i in range(0, len(vect_x) - 1): # importante que llegue hasta una posición anterior
>y_sol_num[i + 1] = y_sol_num[i] + derivative(vect_x[i])* dx
>#Gráficamos
>fig, ax = plt.subplots(1, 1, figsize=(9, 6), dpi=200)
>ax.grid()
>ax.plot(vect_x, y_sol_num, 'm--', label="Solución Númerica")
>ax.plot(vect_x, y_sol_an, 'c-', label="Solución Análitica")
>ax.set_title("Comparación Entre solución númerica y solución análitica")
>ax.set_xlabel("x[m]")
>ax.set_ylabel("y[m]")
>ax.set_xlim([0, 4])
>ax.set_ylim(0, None)
>ax.legend()

>[!Error]- Cálculo de errores
>
>```python
True_error = np.abs(y_sol_an - y_sol_num)
#True_rel_error = True_error / y_sol_an * 100 
fig, ax = plt.subplots(1, 1, figsize=(15, 14), dpi=200)
ax.grid()
ax.plot(vect_x, True_error, '-', label="Error absoluto relativo")
ax.set_title("Comparación Error solución numerica y análitica")
ax.set_xlabel("x[m]")
ax.set_ylabel("y[m]")
ax.set_xlim([0, 4])
ax.set_ylim(0, None)
ax.legend()
>```


