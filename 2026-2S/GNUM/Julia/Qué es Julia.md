# Contexto
## Creación
- Jeff Bezanson
- Stefan Karpinski
- Alan  Edelman
- MIT (Massachusetts Institute of Technology)
Julia empezó en 2009, su primera versión fue lanzada en el 2012, como muchos  lenguajes de programación nació como un proyecto personal y/o grupal. en este caso el proyecto de un grupo de científicos de datos, buscando facilitar la syntax que se utilizaba en ese tiempo con lenguajes como C, sin dejar su velocidad, ya que #python a pesar de ser para "dummies" sacrifica bastante la velocidad de rendimiento, algunos cientificos de la computación vivían trasladandose entre **matlab** por su excelente componente en el álgebra lineal, y algunas veces utilizaban **R** para el análisis de datos másico, la idea de Julia era comprimir lo fuerte de estos 4 lenguajes en uno solo, aunque podían implementarse algoritmos de álgebra lineal en **R**, para algunos programadores esto era "tedioso", misma idea se aplicaba en matlab para el análisis de datos masivo, también Julia nació buscando teniendo un rendimiento tan eficaz buscando evitar depender de librerías escritas en C, cómo es el caso de " #Numpy " en #Python.
## Carácteristicas
### Tolerancia al fallo
A pesar de no tener un control estricto de la distribución (no hay un control estricto de la información que se comparte en el sistema). Aunque no todos los nodos estan activos todo el tiempo, Julia apovecha cuando una comunicación entre los sistemas falla reasigna la tarea, marcandola como *No completada*
## Comunidad "Pequeña"
Aunque tiene competencias que se celebran por parte de comunidades como la computación cientifíca (la cual se celebra en Julio), alardear de tener más de 10mil paquetes (como las librerias de python) el nicho de Julia es relativamente pequeño

>[!Julia]- Paquetes
>Después de abrir Julia en la consola y entrar al gestor de paquetes con `]` , Escribe el comando de instalación seguido del nombre del paquete sin comillas:
>```julia
>pkg> add NombreDelPaquete
>```

## Reutilización y Corrutinas
Julia puede llamar código tanto de #Python como de #C de forma directa, mientras tanto Julia utiliza "Hilos verdes", evitando que al llegar eventos se pueda distribuir y organizar los eventos sin detener el código, así mismo el programa decide y define que evento ignorar y cual atender.

## Qué hay hecho?
- PUMAS: Desarrollo de un software Farmacologico
- Invenio: Optimización redes eléctricas
- BlackRock: Gestión de activos y estudio del mercado bursatil.
- AWS
- Celeste: Proyecto astronomico, mapear el universo a traves de grandes volumenes de datos astronomicos.
- Genie: FrameWork Web, simulación de entrada de datos.
Julia es un lenguaje de proposito general, pero es excelente en su nicho (Ciencía de datos), no es de uso masivo pero es bastante querido para su nicho
# Instalar
Julia actualmente se encuentra en su versión  1.12.7, instalar se vuelve una tarea trivial 
Antes de continuar se comparte el [Repositorio Oficial de Julia](https://github.com/JuliaLang/julia).
para instalar Julia solo se necesita correr el siguiente comando (en #Linux o **macOS**).
```bash
curl -fsSL https://install.julialang.org | sh
```
esto instalara la última versión estable de julia, así como la herramienta`juliaup`.
>[!julia]- Qués es juliaup?
>Juliaup es la herramienta de julia para poder gestionar las versiones del lenguaje de programación.

para iniciar Julia simplemente ingrese `julia`en la terminal y si desea configurar las versiones instaladas ingrese `juliaup --help`.
Si es fan de los cuadernillos de Jupyter, puede notar que Julia no estará en su entorno de #JupyterLab, esto se debe a que no hay un puente o paquete que conecte al lenguaje con el entorno de Jupyter, para ello vamos a instalar el paquete `IJulia` entrando al gestor de paquetes en la terminal de julia (para ingresar al gestor de paquetes se usa `]`)  ingresamos el comando `add IJulia`, ya puede realizar pruebas en sus cuadernillos de jupyter.

--- 
El siguiente [enlace](https://julialang.org/community/) da información sobre los estandares de la comunidad de Julia, además de compartir el mapa de las comunidades locales, las cuales suelen organizar eventos.
![[Pasted image 20260818224250.png]]
## Comunidades:
- **Julia User Group Pittsburgh**
- **Cambridge Area Julia Users Network (C.A.J.U.N.)**
- **Barcelona Julia Meetup**
- **Julia Paris et Environs**
- **JuliaLang Amsterdam**
- **JuliaLang Eindhoven**
- **Julia Berlin Users**
- **Copenhagen Julia Meetup Group**
- **JuliaLang Athens, Greece**
- **JuliaLangJa**
# Clases y Multiple Dispatch en Julia
## Preguntas Guía hasta el momento
- ¿Por qué Julia fue diseñado de esta manera?

- ¿Qué problemas intenta resolver?

- ¿Qué significa que Julia tenga multiple dispatch?

- ¿Cómo afecta el modelo de tipos al diseño de programas científicos?

- ¿Por qué Python tiene un ecosistema de ciencia de datos tan dominante?

- ¿Qué hace NumPy realmente por Python?

- ¿Qué significa que Julia pueda expresar operaciones matemáticas de forma tan directa?

- ¿En qué situaciones tendría sentido elegir Julia en lugar de Python?

Y la Dropsophilia?
# Pregunta Inicial

>[!julia] **¿Cómo influyen la topología de una red neuronal, la dinámica de su actividad y la pérdida previa de neuronas en su resiliencia/desempeño frente a perturbaciones que comprometen su funcionamiento?**

## 1. Enfoques
### 1.1 Ataques como propagación de una alteración
Analizar como una alteración puede modificar:
1. La conectividad entre neuronas
2. La intensidad de la pertubación neuronal.
3. La capacidad de escoger rutas para solucionar.
4. Capacidad para compensar la perdida funcional.
Teniendo en cuenta los siguientes casos:
- **Propagación del daño estructural:** Neuronas que pasan de un estado activo a un estado dañado o incluso inactivo
- **Propagación de la alteración funcional:** Sigue existiendo la neurona, pero la actividad cerebral se modifica a causa de la alteración inicial.
### 1.2 Ciberataques contra un modelo computacional del cerebro
- La manipulación de señales de entrada.
- La modificación de parámetros del modelo.
- La perdida de componentes simulados
- La alteración entre conexiones, neuronas y su **sinapsis**
En este caso, el ataque ocurre sobre el modelo computacional, no sobre el cerebro biológico.
## 2. Estructura cerebral de la Drosophilia-Melanogaster.
### Modulo 1: Comprender el modelo del cerebro de la mosca
La idea principal es comenzar con una red reducida utilizando los Datos Biologicos dados por [Flywire]([https://codex.flywire.ai/](https://codex.flywire.ai/)), se va a buscar elegir un circuito asociado a una función medible, entendiendo que funcion tiene este y los impactos posibles en el funcionamiento de la misma.
Algunos *posibles modelos* son:

| Modelo                                          | Ventajas                                                            | Limitaciones                                                                                            |
| ----------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| Red neuronal abstracta                          | Permite desarrollar y validar rápidamente las ecuaciones.           | No se puede orientar a una función biologica                                                            |
| Circuito neuronal simplificado de _#Drosophila_ | Facilita relacionar la dinámica con una función biológica concreta. | Requiere seleccionar y justificar el circuito.                                                          |
| Subred derivada del conectoma                   | Permite estudiar topología y conectividad con mayor realismo.       | Requiere procesamiento de datos y más capacidad computacional.                                          |
| Cerebro completo                                | Mayor alcance estructural.                                          | Modelar la dinámica de un cerebro completo es absurdamente complejo y se necesita simplificar el mismo. |
### Modulo 2: El modelo del Grafo Neuronal
Representar la red total y sus subredes como un grafo dirigido:
$$G=(N,S)$$
Donde:
- $N$ representa el conjunto de neuronas *(Vertices)*
- $E$ Representa el conjunto de conexiones "Sinapsis" *(Aristas)*
Además se puede utilizar una matriz de conectividad, la cual se definirá como:
$$A = [a_{ij}]$$
donde $a_{ij}$ representa la conexión de la neurona $j$ con la neurona $i$, sus valores se definiran como los siguientes:
$$a_{ij}=\begin{cases}1 \quad \text{Si existe conexión de la neurona } j \text{ hacía la neurona } i\\ 0\quad \text{en caso contrario}\end{cases}$$
También se puede utilizar una Matriz de pesos (ponderado).$$w_{ij} = \begin{cases} \text{peso sináptico } (j \to i), & \text{si } a_{ij} = 1 \\ 0, & \text{si } a_{ij} = 0 \end{cases}$$
- **Excitatorio ($w_{ij} > 0$):** Incrementa la activación de la neurona destino $i$.
- **Inhibitorio ($w_{ij} < 0$):** Reduce la activación de la neurona destino $i$.
- **Sin conexión ($w_{ij} = 0$):** Ausencia de flujo de información.
Los pesos pueden representar la eficacia sináptica.
>[!Julia] Hipotesis
>**¿La vulnerabilidad del sistema depende de la cantidad de neuronas afectadas o de cuáles son las neuronas afectadas?**
Dos redes pueden perder exactamente el mismo número de neuronas y experimentar consecuencias muy diferentes.
Una perturbación que afecta a neuronas periféricas puede ser menos perjudicial que otra que compromete componentes centrales de un circuito, aunque ambas eliminen el mismo número de nodos.
### Módulo 3: Modelar la actividad neuronal mediante una ODE o UDE
Una ODE describe cómo evoluciona una variable de estado con el tiempo.
**Ejemplo:**
$$x_i(t)=\text{estado de actividad de la neurona } i \text{ en el instante t}$$
en este caso se podría interpretar como la cantidad de impulsos eléctricos ( #spikes), aquí nos toca decidir si lo expresamos en $Hz$ o entre 0 y 1 (actividad neuronal normalizada).
>[!question] Aquí si me gustaría que pudieran presentar otras opciones para la variable de estado.
>Por ejemplo $$y_{i}=\text{ Puede representar la actividad promedia de muchas neuronas en una región del modelo}$$

una ecuación diferencial simplificada para la dinámica de la subred puede ser:
$$\tau_i\dfrac{dx_i(t)}{dt}=-x_i(t)+\phi\left(\sum_{j=1}^Nw_{ij}x_j+I_i(t)\right)$$
Donde: 

| **Término**                    | **Denominación**       | **Función en la red**                                                                                                                                                 |
| ------------------------------ | ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| $x_i(t)$                       | Variable de estado     | Nivel de activación de la neurona $i$ en el instante $t$.                                                                                                             |
| $\frac{dx_i}{dt}$              | Tasa de cambio         | Velocidad y dirección con la que cambia la actividad de la neurona.                                                                                                   |
| $\tau_i$                       | Constante de tiempo    | Determina la _inercia_ o rapidez con la que la neurona responde. Un $\tau_i$ grande suaviza cambios rápidos; un $\tau_i$ pequeño reacciona casi instantáneamente.     |
| $-x_i(t)$                      | Término de decaimiento | Fuerza de fuga o relajación (_leakage_). Sin estimulación, la neurona vuelve de forma natural a su estado de reposo ($x_i = 0$).                                      |
| $\sum_{j=1}^{N} w_{ij} x_j(t)$ | Entrada recurrente     | La suma ponderada del impacto de todas las neuronas del grafo que conectan hacia $i$ (usando la convención $j \to i$ del Módulo 2).                                   |
| $I_i(t)$                       | Entrada externa        | Estímulos o señales provenientes de fuera del grafo (como sensores, datos de entrada o inputs de otros módulos).                                                      |
| $\phi(\cdot)$                  | Función de activación  | Transforma la suma de entradas en una salida no lineal (ej. Sigmoide, ReLU o Tanh), acotando la respuesta e introduciendo comportamiento **no lineal** en el sistema. |
La parte izquierda de la inecuación representa su velocidad de cambio respecto a un $\tau_i$ donde se explica como que tan suave o rapida se desea la respuesta en el instante de tiempo, esto será igual al termino de relajación, si la neurona no recibe estimulo ($\phi$) la ecuación va a decaer exponencialmente a cero (va a volver a su reposo), este mismo termino de estimulo se acota ya que ningun sistema puede crecer infinitamente, a veces se puede visualizar de la siguiente manera, $\phi(U_i) \in [0, 1]$ donde habla de la probabilidad de activarse en un momento dado, pero en general eso limita modelo, en este caso se podría ver como la tasa/frecuencia de disparo (spikes).
#### Forma Vectorial
Si se agrupan los estados de las $N$ neuronas en un vector $x(t) = [x_1(t), \dots, x_N(t)]^T$, todo el sistema de $N$ ecuaciones diferenciales ordinarias (ODEs) acopladas se escribe de forma compacta como:
$$\mathbf{T} \frac{d\mathbf{x}}{dt} = -\mathbf{x}(t) + \Phi \big( W \mathbf{x}(t) + \mathbf{I}(t) \big)$$
donde $\mathbf{T} = \text{diag}(\tau_1, \dots, \tau_N)$ es la matriz de constantes temporales, $W$ es la matriz de pesos del Módulo 2 y $\Phi$ aplica la función de activación elemento a elemento.
### Módulo 4: modelar la propagación del daño
La variable de estado para esta parte se puede definir como:
$$d_i(t)\in[0,1]$$
Donde: 
- Donde $d_i=0$ la neurona no recibió daño en el sentido que lleguemos a definirla.
- $d_i=1$ La neurona alcanza el nivel máximo de daño (podría ser un colapso).
- El resto de valores representan daños **parciales**
Una formulación inicial:
$$ \frac{dd_i}{dt} = (1-d_i) \left[ u_i(t)+ \beta\sum_{j=1}^{N}a_{ij}d_j \right] -\gamma d_i $$
La ecuación expresa como gobierna el nivel de daño $d_i(t)\in[0,1]$ de cada neurona $i$ a lo largo del tiempo.

| **Término**             | **Significado**                              | **Función en la red**                                                                                                                                       |
| ----------------------- | -------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| $d_i(t)$                | Nivel de daño                                | Estado de degradación de la neurona $i$ en el instante $t$ ($0 = \text{sana}$, $1 = \text{daño máximo}$).                                                   |
| $\frac{dd_i}{dt}$       | Velocidad de propagación                     | Ritmo al que se degrada o se recupera la neurona $i$.                                                                                                       |
| $(1 - d_i)$             | Factor de capacidad/saturación               | Mantiene $d_i \le 1$. A medida que la neurona se acerca al daño máximo ($d_i \to 1$), la capacidad de sufrir _más_ daño disminuye a cero.                   |
| $u_i(t)$                | Perturbación / Insulto directo (daño previo) | Estrés exógeno aplicado directamente a la neurona $i$ (ej. isquemia local, trauma, toxina focal).                                                           |
| $\beta \sum a_{ij} d_j$ | Término de propagación de red                | **Es la "propagación tipo contagio":** el daño de las neuronas vecinas $j$ influye sobre $i$ a través de las conexiones estructurales del grafo ($a_{ij}$). |
| $\beta$                 | Coeficiente de contagio                      | Controla qué tan "transmisible" o virulento es el daño a través de la topología del grafo.                                                                  |
| $\gamma d_i$            | Término de reparación                        | Capacidad de resiliencia o mecanismos celulares de limpieza/reparación natural. Resta daño proporcionalmente al nivel actual.                               |
## 3. Respecto a las UDES
Las ODE permiten formular dinámicas explícitas, mientras que las UDE permiten combinar ecuaciones diferenciales conocidas con componentes parametrizados o aprendidos a partir de datos (básicamente nos permite trabajar mejor con el aprendizaje de los datos, se pueden entrenar).
Permite tener un confianza en que el termino adicional de la UDE va a evitar el aumento del error sin necesidad de conocer todos los mecanismos del sistema.
### 3.1. El problema de las ODE tradicionales y su alternativa
$$ \frac{dx}{dt}=f(x,W,I) $$
En este caso aunque conocemos varias cosas sobre le cerebro es excesivamente complejo diseñarlo en su totalidad, porque simplemente no conocemos todos los términos que aportan y son relevantes.
Por otro lado la UDE se puede formular de la siguiente forma:
$$\frac{dx}{dt} = f_{\text{conocido}}(x,W,I) + g_{\theta}(x,W,I) $$
Donde:

- $(f_{\text{conocido}}$) representa la dinámica explícita.
- ($g_{\theta}$) representa una función parametrizada que aproxima las dinámicas no conocidas.
- ($\theta$) representa los parámetros que deben aprenderse o calibrarse.

La función $(g_{\theta})$ podría implementarse mediante una red neuronal u otro modelo parametrizado.
# Preguntas
- **¿Cómo influyen la topología de una red neuronal, la dinámica de su actividad y la pérdida previa de neuronas en su resiliencia/desempeño frente a perturbaciones que comprometen su funcionamiento?**
- **Cómo está organizada la red neuronal a trabajar?**
- **¿La vulnerabilidad del sistema depende de la cantidad de neuronas afectadas o de cuáles son las neuronas afectadas?**

## 5. Bibliografía Recomendada y Fuentes de Soporte

A continuación se presentan las referencias fundamentales que sustentan el marco conceptual del conectoma, la dinámica de propagación de perturbaciones mediante **ODEs/UDEs** y el análisis estadístico de redes complejas.

### 5.1. Conectómica de Drosophila melanogaster y Redes Complejas

* **Dorkenwald, S., et al.** (2024). *Neuronal wiring diagram of an adult brain*. **Nature**, 634, 124–138.  
  * **Plataforma de Consulta:** [FlyWire Codex](https://codex.flywire.ai/) | [Leer Artículo en Nature](https://doi.org/10.1038/s41586-024-07558-y)

* **Lin, A., et al.** (2024). *Network statistics of the whole-brain connectome of Drosophila*. **Nature**, 634, 153–165.  
  * **Acceso Abierto (PMC):** [PMC2992341 / Artículo Completo](https://pmc.ncbi.nlm.nih.gov/articles/PMC2992341/) | [Leer Artículo en Nature](https://doi.org/10.1038/s41586-024-07968-y)

* **Latora, V., & Marchiori, M.** (2001). *Efficient Behavior of Small-World Networks*. **Physical Review Letters**, 87(19), 198701.  
  * [Ver en Physical Review Letters](https://doi.org/10.1103/PhysRevLett.87.198701)

---

### 5.2. SciML y Dinámica de Perturbación

* **Rackauckas, C., et al.** (2020). *Universal Differential Equations for Scientific Machine Learning*. **arXiv preprint**, arXiv:2001.04385.  
  * [Leer Preprint en arXiv](https://arxiv.org/abs/2001.04385)

* **Pappu, K., Joshi, P. D., Dandekar, R. A., Dandekar, R., & Panat, S.** (2025). *Understanding Malware Propagation Dynamics through Scientific Machine Learning*. **arXiv preprint**, arXiv:2507.07143.  
  * [Leer Preprint en arXiv](https://arxiv.org/abs/2507.07143)

* **López Madejska, V. M., López Bernal, S., Martínez Pérez, G., et al.** (2024). *Impact of neural cyberattacks on a realistic neuronal topology from the primary visual cortex of mice*. **Wireless Networks**, 30, 7391–7405.  
  * [Leer Artículo en Springer](https://doi.org/10.1007/s11276-024-03712-4)

---

### 5.3. Métodos Estadísticos y Análisis de Redes (Soporte Práctico)

* **Kolaczyk, E. D., & Csárdi, G.** (2020). *Statistical Analysis of Network Data with R* (2nd ed.). Springer.  
  * **Aporte:** Manual de referencia para la caracterización estadística de grafos dirigidos, modelos nulos, centralidad y propagación epidémica sobre redes.
  * **Recursos:** [Descargar PDF del Libro](https://www.dropbox.com/scl/fi/dygd1irtgbr7zk4yghoph/2020-Kolaczyk-and-Cs-rdi-Statistical-Analysis-Of-Network-Data-With-R.pdf?rlkey=kzgyrc9pnyx5elzz0p082aepb&e=1&dl=0) | [Repositorio GitHub del Libro (`sand`)](https://github.com/kolaczyk/sand)

* **Sosa, J.** (2024). *Notas del curso de Manejo y Análisis de Redes*.  
  * **Aporte:** Guías metodológicas y fundamentos conceptuales para el procesamiento e inferencia de grafos complejos.
  * [Sitio Web del Curso de Redes](https://sites.google.com/view/juansosa/networks)








Tags: #Tipado_Dinámico #python #Numpy #C #Linux #JupyterLab  #Julia #JupyterLab #Drosophila #spikes