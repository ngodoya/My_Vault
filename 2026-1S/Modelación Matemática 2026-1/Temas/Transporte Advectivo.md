Para Recocerlo hay que ver las **EDP** de la forma:
$$
u \dfrac{d\phi}{dx} \quad \text{Fijese si tiene un termino de velocidad}
$$
Utilizamos Diferencias Finitas en este caso
# Notación
Difusión
$$\dfrac{\partial^2y}{\partial t^2}$$

* Esq. hacía adelante  $$  \dfrac{d\phi}{dx} \approx \dfrac{\phi_{i+1}-\phi_{i}}{\Delta x} $$ #Esquemas_Int 
- Esq. hacía atrás $$  \dfrac{d\phi}{dx} \approx \dfrac{\phi_{i}-\phi_{i-1}}{\Delta x} $$
- Otra forma (Más compleja pero linda)  Esq. Central $$\dfrac{d\phi}{dx} \approx \dfrac{\phi_{i+1}-\phi_{i-1}}{2\Delta x}  $$
# Upwind Qué es?
tenga en cuenta que muchas veces vamos a necesitar escoger el esquema dependiendo de lo que tenemos por ejemplo un flujo si no conocemos el flujo del futuro porque utilizaríamos un Esq hacía adelante

# INTEGRACIÓN TEMPORAL 
$$Co \leq 1.0$$
Condicionalmente estable
* Implicito
Incodicionalmente estable

> [!note]
> Repase los cuadernillos  de introducción a los modelos con EDP


> [!info]
Ejercicio:



Tags: #Esquemas_Int
