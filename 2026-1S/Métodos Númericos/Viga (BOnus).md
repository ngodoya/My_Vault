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