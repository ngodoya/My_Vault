# La función Sigmoide (La útima capa)

El modelo de la regresión Logistica hace uso de un grupo de funciones conocidas  como funciones sigmoides (hay una matematica detras la cual busca encontrar en que vamos a evaluar la función sigmoide) tiene forma de S y convierte los valores limitandolos entre valores de 0 y 1.
**Ejemplos:**
- Función logística: $$\sigma(z) = \dfrac{1}{1+e^{-z}}$$ donde $z$ se define como los datos (modificados por una función)
- Tangente Hiperbólica (Tanh):$$tanh(x)=\dfrac{e^x-e^{-x}}{e^x+e^-x}=\dfrac{senh(x)}{cosh(x)}$$
	Donde su imagen esta en el dominio $[-1;1]$
- Arcotangente $f(x)=arctan(x)$
- Curva de Gompertz: $$f(t)=ae^{-be^{-ct}}$$
	- $a$ es una asíntota, ya que $$\lim_{t\to0}ae^{-be^{-ct}}=ae^0=a$$
	- _b_ establece el desplazamiento a lo largo del eje x (traduce el gráfico a la izquierda o derecha)
	- _c_ establece la tasa de crecimiento (escala _y_)
## Modelo aplicado en la SIgmoide
Realmente el modelo es $$z=\beta_0+\beta_1x_1+\cdots+\beta_nx_n$$
y después:$$p=σ(z)$$
>[!numpy] Note que para encontrar el modelo puede hacer uso de una regresión por mínimos Cuadrados
>>[!python]- Cuando Realizamos Código de este estilo es util ver los paquetes y modulos por lo que son "¿Quién es responsable de esto?":
>>Ejemplos:
>>- Models se encarga del modelo, no hace cálculos de precisión, no sabe hace optimización, los métodos numericos en especifico se guardan dentro de su area, esto se hace con la intención de reutilizar los mismmos modelos
>>- 

Tags: #sigmoide