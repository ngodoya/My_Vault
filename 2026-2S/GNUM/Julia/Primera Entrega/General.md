Inicialmente antes de trabajar con la Matriz obtenida en **Flywire** la cual tiene una cantidad exhaustiva de datos y se visualiza de la siguiente forma:

| pre                                 | post                                 | neuropilo                                                          | n# de sinápsis                                                                        | neurotransmisor                                                                |
| ----------------------------------- | ------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| id de la neurona que envía la señal | id de la neurona que recibe la señal | La región física específica del cerebro donde ocurre ese contacto. | Cuántos puntos de contacto físico hay entre ambas neuronas _dentro de ese neuropilo_. | La sustancia química que utiliza *pre* para saltar de donde hasta hasta *post* |
>[!warning]- Neuropilo
>En nuestro primer modelo matemático no nos interesa el barrio en la que las ramas de las neuronas hacen contacto (neuropilo), solo es relevante la fuerza total que A ejerce en B, por lo mismo, el script agrupa todas las filas que comparten el mismo `(pre, post)`, elimina la columna `neuropilo` y **suma las sinapsis** ($4 + 6 + 2 = 12$).

De este proceso salen las siguientes matrices:

| Matriz                                 | Definición                                          | Qué responde                      |
| -------------------------------------- | --------------------------------------------------- | --------------------------------- |
| $A$ (adyacencia)                       | $a_{ij} = 1$ si existe $j \to i$                    | ¿Hay conexión?                    |
| $\lvert W\rvert$ (ponderada sin signo) | $\lvert w_{ij}\rvert$ = nº de sinapsis de $j \to i$ | ¿Qué tan fuerte?                  |
| $W$ (ponderada con signo)              | $w_{ij} = \pm$ nº de sinapsis                       | ¿Qué tan fuerte y en qué sentido? |
El signo sale del neurotransmisor de la neurona presináptica: 

| NeuroTransmisor | Signo |
| --------------- | ----- |
| GABA            | **-** |
| Glutamato       | **-** |
| acetilcolina    | **+** |
| dopamina        | **+** |
| serotonina      | **+** |
| octopamina      | **+** |
Es la regla del modelo de [Shiu et al](https://www.nature.com/articles/s41586-024-07763-9#Fig1). (A _Drosophila_ computational brain model reveals sensorimotor processing) En los dos archivos cada neurona tiene un solo neurotransmisor.
Para esta primera fase se realizo una análisis de la dinámica del cerebro al recibir un estimulo, 21 **neuronas** reciben un estimulo externo a $I(t)$ a 150(Hz) (ciclos por segundo), después de eso 343 **interneuronas** se activan para transportar el estimulo, formando la red intermedia que **procesa** y **transmite** la señal.
La señal es transmitida a **MN9** la cual es neurona de salida (motora) la cual procesa la señal y dispara para ordenar la extensión de la probóscide (la trompa de la mosca).
>[!julia] $i \rightarrow j$ o $j \rightarrow i$
>Con Graphs.jl: `SimpleDiGraph` + `adjacency_matrix` da $A$, y `SimpleWeightedDiGraph(pre, post, peso)` + `weights` da $W$. Graphs.jl usa la convención $i \to j$; el documento usa $j \to i$, por eso el código traspone.
```julia
# 1. Crea la estructura del grafo dirigido (solo conexiones, sin pesos)
g = SimpleDiGraph(n_neuronas)
for (u, v) in zip(pre, post)
    add_edge!(g, u, v)
end

# 2. Extrae la matriz de adyacencia (1 donde hay flecha, 0 donde no) y la traspone
A = Float64.(adjacency_matrix(g)')
```
Además de tener en cuenta que se hace un filtro para las matrices donde todas las neuronas que tengan  sinapsis $\geq$ 5, esto se hace debido a un filtro donde la comunidad cientifica concluye que es el estandar.
**Conservar la estructura funcional:** Como demuestra el análisis de la subred, este filtro elimina el **64.9 %** de las conexiones débiles pero conserva el **90.6 %** del total de sinapsis, dejando intactas las rutas principales (como la vía azúcar $\to$ MN9 en 2 saltos). 
>[!note] Nota
>Aunque sirve para estudiar la estructura, para simular actividad dinámica conviene usar el dataset sin filtro porque ese 9.4 % de sinapsis eliminadas altera la tasa de disparo de varias neuronas).
# 2. ODE
El script resuelve la siguiente ecuación diferencial ordinaria (ODE) de tasa de disparo (_firing-rate model_):
$$\tau_i\dfrac{dx_i(t)}{dt}=-x_i(t)+\phi\left(\sum_{j=1}^Nw_{ij}x_j+I_i(t)\right)$$
## 2.1 ¿Qué es el modelo LIF?

A diferencia de la ODE (que solo calcula un promedio continuo), el LIF simula **neurona por neurona y milisegundo a milisegundo**:

- **Integración (_Integrate_):** Cada vez que una neurona recibe una señal de otra, su voltaje interno sube (si es excitatoria) o baja (si es inhibitoria).
- **Fuga (_Leaky_):** Si no recibe señales nuevas, su membrana tiene una "fuga" natural y el voltaje vuelve lentamente a su estado de reposo.
- **Disparo (_Fire_):** Cuando el voltaje acumulado cruza un umbral crítico, la neurona lanza un pulso eléctrico discreto (un _spike_ o potencial de acción) hacia sus vecinas y su voltaje se reinicia de golpe.
>[!scipy] `Tsit5`
>**¿Por qué `Tsit5()` con `tstops=[0.1, 0.6]`?** `Tsit5()` (Tsitouras 5/4) es el método Runge-Kutta explícito estándar de alto rendimiento en `DifferentialEquations.jl` para ecuaciones no rígidas. Como el estímulo $I(t)$ se enciende y apaga de golpe en $0.1\text{ s}$ y $0.6\text{ s}$ (discontinuidades), `tstops=[0.1, 0.6]` obliga al integrador a detenerse exactamente en esos instantes para no perder precisión.
**El techo artificial de la sigmoide ($\approx 76.4\text{ Hz}$):**

- En el modelo LIF real, si una neurona recibe mucha excitación, puede disparar a **120, 150 o hasta 180 Hz** (solo limitada por su periodo refractario de unos pocos milisegundos).
- En cambio, la ODE utiliza una función matemática sigmoide ($\phi_0$) que tiene un límite superior fijo calibrado en **$76.4\text{ Hz}$**. Por eso, en la gráfica de puntos, todas las neuronas que en el LIF disparan por encima de 80 Hz quedan aplastadas formando una línea horizontal plana en 76 Hz (el RMSE de $27.7\text{ Hz}$ viene en gran parte de ese corte).
**Pérdida de la dinámica de pulsos y tiempos de espera:**
- La ODE reemplaza los disparos individuales (_spikes_) por una **tasa de disparo continua promedio** y asume que todas las neuronas responden con una misma curva sigmoide estándar.
- En el LIF real, la sincronización exacta de cuándo llegan los pulsos, los periodos refractarios después de cada disparo y el umbral de voltaje de cada neurona generan respuestas no lineales que una sigmoide simple no alcanza a capturar.