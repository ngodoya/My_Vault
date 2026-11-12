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
>[!julia]- $i \rightarrow j$ o $j \rightarrow i$
>Con Graphs.jl: `SimpleDiGraph` + `adjacency_matrix` da $A$, y `SimpleWeightedDiGraph(pre, post, peso)` + `weights` da $W$. Graphs.jl usa la convención $i \to j$; el documento usa $j \to i$, por eso el código traspone.
