# Formulas
- **True Error:** $Value_{real} - Approximation_{Value}$
- **Error Relativo Absoluto $\epsilon_t$:** $\dfrac{Value_{real} - Approximation_{Value}}{Value_{real}}$
- **Approximate Relative Error $\epsilon_a$:** $\dfrac{Current_{Approximation} - Previous{Approximation}}{Current{Approximation}}$
>[!Tip]- Series de Taylor y relación $h^{n+1}$
> El error es proporcional a: $h^{n+1}$ (En las series de Taylor)
> Es útil, para terminar el código poner una condición de $$\epsilon_a \leq \epsilon_s$$ donde $\epsilon_s$ es el porcentaje de error relativo deseado.
> 


Tags: #Errores