# Versión simplificada: matrices, ODE, continuidad y los dos datasets

> [!julia] Resumen
> 1. La **matriz de adyacencia** $A$ dice *quién* se conecta con quién; la **matriz ponderada con signo** $W$ dice *cuánto* y *en qué sentido* (excita o inhibe). La actividad la define $W$, no $A$.
> 2. La **ODE** del Módulo 3 es $\tau\,\dot x = -x + \phi(\kappa W x) + I(t)$. La **UDE** es esa misma ecuación con un término más, $g_\theta$.
> 3. Hay puntos donde las funciones o el grafo no están definidos. Cada uno tiene un síntoma medible y un arreglo.
> 4. El filtro de FlyWire (≥ 5 sinapsis) quita el 65 % de las conexiones de la subred pero solo el 9 % de las sinapsis.

Todos los números salen de correr los cuatro scripts de esta carpeta con tus dos archivos (`connections_princeton.csv.gz` y `connections_princeton_no_threshold.csv.gz`) sobre el circuito de 365 neuronas azúcar → MN9.
>[!note]- MN9
>Las **neuronas MN9** (_Motor Neuron 9_) ==son un par de **neuronas motoras** identificadas en el sistema nervioso central de la mosca de la fruta== (_Drosophila melanogaster_), cuya función principal es **controlar la extensión de la probóscide** (el órgano de alimentación del insecto) para iniciar la ingesta de alimento.
## 0. Cómo correrlo

```bash
cd ODE_simple
julia --project=. -e 'using Pkg; Pkg.instantiate()'       # una sola vez
julia --project=. 1_matrices_y_datasets.jl                 # necesita los dos .csv.gz (ver abajo)
julia --project=. 2_ode.jl
julia --project=. 3_continuidad.jl
julia --project=. 4_de_ode_a_ude.jl
```

El script 1 lee los dos archivos grandes. Ponlos en `datos/` con esos nombres, o indica la ruta:
`export DATOS_FILTRADO=/ruta/connections_princeton.csv.gz` y `export DATOS_SIN_FILTRO=/ruta/connections_princeton_no_threshold.csv.gz`.
Los scripts 2, 3 y 4 no los necesitan: usan las tablas pequeñas que ya están en `datos/` (`aristas_filtrado.csv`, `aristas_sin_filtro.csv`, `aristas_repo.csv`).

| Archivo | Qué hace |
|---|---|
| `comun.jl` | Constantes, `matrices()`, `phi`, `phi0`, `ode!` |
| `1_matrices_y_datasets.jl` | $A$ y $W$ con Graphs.jl para los dos datasets; comparación |
| `2_ode.jl` | La ODE con cada matriz y con cada dataset |
| `3_continuidad.jl` | Puntos no definidos / no continuos y sus arreglos |
| `4_de_ode_a_ude.jl` | La UDE como "ODE + un término" |

## 1. Las tres matrices

Cada renglón de los archivos de FlyWire es `(pre, post, neuropilo, nº de sinapsis, neurotransmisor)`. Sumando los neuropilos de cada par queda una tabla de aristas `pre, post, sinapsis, nt`. De esa tabla salen:

| Matriz | Definición | Qué responde |
|---|---|---|
| $A$ (adyacencia) | $a_{ij} = 1$ si existe $j \to i$ | ¿Hay conexión? |
| $\lvert W\rvert$ (ponderada sin signo) | $\lvert w_{ij}\rvert$ = nº de sinapsis de $j \to i$ | ¿Qué tan fuerte? |
| $W$ (ponderada con signo) | $w_{ij} = \pm$ nº de sinapsis | ¿Qué tan fuerte y en qué sentido? |

El signo sale del neurotransmisor de la neurona presináptica: GABA y glutamato inhiben (−); acetilcolina, dopamina, serotonina y octopamina excitan (+). Es la regla del modelo de Shiu et al. En los dos archivos cada neurona tiene un solo neurotransmisor.

Con Graphs.jl: `SimpleDiGraph` + `adjacency_matrix` da $A$, y `SimpleWeightedDiGraph(pre, post, peso)` + `weights` da $W$. Graphs.jl usa la convención $i \to j$; el documento usa $j \to i$, por eso el código traspone.

### Qué muestra `figuras/1_matrices_y_datasets.png`

| Panel | Qué representa |
|---|---|
| A filtrado / A sin filtro | Cada punto negro es una conexión $j \to i$. Columnas = neurona que envía, filas = neurona que recibe. Las neuronas están ordenadas por fuerza de salida, por eso la izquierda es más densa |
| W filtrado / W sin filtro | Lo mismo, pero el color es el peso: rojo excita, azul inhibe, más intenso = más sinapsis. Una columna toda roja o toda azul es una neurona excitatoria o inhibitoria |
| Distribución de pesos | Cuántas conexiones hay con 1, 2, 3… sinapsis (eje vertical logarítmico). La línea punteada es el umbral del filtro: todo lo que está a su izquierda desaparece en el dataset filtrado |
| Conexiones de entrada por neurona | Cada punto es una neurona: cuántas conexiones recibe sin filtro (horizontal) y con filtro (vertical). Todos caen muy por debajo de la diagonal: el filtro quita muchas conexiones |
| Sinapsis de entrada por neurona | Igual, pero contando sinapsis. Aquí casi todos están sobre la diagonal: se pierden pocas sinapsis |
| Efecto del filtro en cada neurona | Histograma del % de sinapsis de entrada que pierde cada neurona |

## 2. ¿Qué matriz define la actividad?

Se corre la misma ODE cambiando solo la matriz y se compara la tasa de cada neurona con la del modelo de disparos (LIF) sobre el mismo dataset (sin filtro, azúcar a 150 Hz):

| Matriz usada en la ODE | Correlación con el LIF | Error (RMSE, Hz) | Tasa media (Hz) |
|---|---|---|---|
| $A$ (solo unos y ceros) | 0.23 | 41.9 | 73.5 |
| $\lvert W\rvert$ (sinapsis, sin signo) | 0.21 | 42.2 | 74.2 |
| $W$ (sinapsis con signo) | **0.86** | **27.7** | 42.8 |
| LIF (referencia) | 1 | 0 | 59.8 |

- Con $A$ o con $\lvert W\rvert$ todas las conexiones excitan: la red entera se va al máximo (≈ 74 Hz en casi todas las neuronas) y no se parece a nada.
- Agregar el número de sinapsis **sin** el signo no mejora (0.23 → 0.21). Lo que cambia todo es el signo.
- Conclusión: $A$ define las conexiones; **$W$ con signo define la actividad**. La inhibición es lo que le da estructura.

En `figuras/2_ode.png`: arriba a la izquierda, la salida MN9 en el tiempo con cada matriz; los tres paneles de puntos comparan, neurona por neurona, la tasa de la ODE (vertical) con la del LIF (horizontal). Sobre la diagonal = acierto. Con $A$ y $\lvert W\rvert$ los puntos forman una línea horizontal (todas saturadas); con $W$ siguen la diagonal hasta 76 Hz, que es el tope de la sigmoide.

## 3. Cómo se modela la ODE

$$\tau\,\frac{dx_i}{dt} = -x_i + \phi\Big(\kappa \sum_j w_{ij}\,x_j\Big) + I_i(t)$$

| Pieza | Significado | Valor |
|---|---|---|
| $x_i(t)$ | Tasa de disparo de la neurona $i$ (Hz) | variable de estado |
| $-x_i$ | Fuga: sin entrada, la tasa decae a 0 | — |
| $\mu_i = \kappa\sum_j w_{ij}x_j$ | Entrada sináptica media (mV) | $\kappa = 0.275\ \text{mV} \times 0.005\ \text{s}$ |
| $\phi$ | Función de activación (convierte mV en Hz) | sigmoide: $r_{max} = 76.4$ Hz, $\theta = 14.4$ mV, $s = 4.5$ mV |
| $\tau$ | Qué tan rápido responde | 9.9 ms |
| $I_i(t)$ | Estímulo: las 21 neuronas de azúcar a 150 Hz entre 0.1 y 0.6 s | — |

$\kappa$ no es un parámetro libre: en el LIF cada disparo suma 0.275 mV por sinapsis y ese efecto dura 5 ms. Los cuatro parámetros de $\phi$ y $\tau$ se calibraron contra el LIF en el proyecto completo.

En código es una función de tres líneas (`ode!` en `comun.jl`):

```julia
function ode!(dx, x, p, t)
    mu = KAPPA .* (p.M * max.(x, 0.0))          # entrada sináptica de cada neurona
    dx .= (-x .+ p.f.(mu) .+ p.I(t)) ./ TAU     # fuga + activación + estímulo
end
```

## 4. De la ODE a la UDE

La derivación son tres pasos:

1. **Escribir la ODE como "lo que sé":** $\tau\dot x = -x + \phi(\mu) + I$.
2. **Reconocer qué le falta.** La ODE se equivoca de dos formas visibles: se satura en 76 Hz aunque en el LIF haya neuronas que pasan de 150 Hz, y trata igual a una neurona que recibe su entrada por muchas sinapsis débiles que a una que la recibe por pocas muy fuertes.
3. **Sumar un término que se aprende de los datos:**

$$\tau\,\frac{dx_i}{dt} = -x_i + \phi(\mu_i) + \underbrace{g_\theta(\mu_i, \sigma_i)}_{\text{red neuronal}} + I_i(t), \qquad \sigma_i = \sqrt{\kappa_2 \sum_j w_{ij}^2\,x_j}$$

$\sigma_i$ es la fluctuación de la entrada (usa $W^2$): es grande cuando la entrada llega por pocas sinapsis fuertes. $g_\theta$ es una red de 2 → 16 → 16 → 1, la misma para todas las neuronas (341 parámetros en total, contando los 4 físicos).

En código la diferencia es una línea (`ude!` en el script 4):

```julia
dx .= (-x .+ phi_u.(mu) .+ g(mu, sigma) .+ p.I(t)) ./ tau_u     # ← ODE + g_θ
```

Si $g_\theta = 0$ la UDE **es** la ODE. Por eso se dice que "se deriva" de ella: no se reemplaza nada, se agrega.

Resultado (la red se entrenó solo con la tabla del repositorio; los otros dos datasets nunca los vio):

| Dataset | RMSE ODE (Hz) | RMSE UDE (Hz) | MN9 LIF | MN9 ODE | MN9 UDE |
|---|---|---|---|---|---|
| repo | 9.9 | 3.3 | 70.6 | 76.4 | 68.6 |
| filtrado | 24.1 | 8.9 | 111.3 | 76.4 | 92.0 |
| sin filtro | 27.2 | 10.0 | 115.3 | 76.3 | 92.9 |

El error baja a cerca de un tercio en los tres. En `figuras/4_de_ode_a_ude.png`, el primer panel muestra qué aprendió la red: la curva negra punteada es $\phi$ (se aplana en 76 Hz); las de colores son $\phi + g_\theta$ para tres valores de $\sigma$ (no se aplanan, y con $\sigma$ grande la tasa es menor para la misma entrada).

## 5. Continuidad y puntos no definidos

| Dónde | Qué pasa | Síntoma medido | Arreglo |
|---|---|---|---|
| $\phi$ = escalón | Salta en $\mu=\theta$: no es continua | El integrador necesita 32 165 pasos y rechaza 87 175 (la sigmoide: 249 y 52) | Usar una función continua |
| $\phi$ = curva f–I exacta del LIF, $1/(t_{ref}+t_m\ln\frac{\mu}{\mu-7})$ | Para $\mu < 7$ mV el logaritmo recibe un negativo: **no está definida** (Julia da `DomainError`). En $\mu = 7$ divide por cero. Justo encima, la pendiente es 622 Hz/mV y crece sin límite | 2 979 pasos, 2 762 rechazados | Definirla por tramos (0 bajo el umbral) o cambiarla por la sigmoide |
| $\phi$ = ReLU | Continua, pero con esquina (no derivable ahí) y sin tope | — | Sirve para simular; para entrenar es mejor una función suave |
| $\phi$ = sigmoide | Definida, continua y derivable en todo $\mathbb{R}$; pendiente máxima 4.24 Hz/mV | 249 pasos | Es la del documento. Su defecto es otro: $\phi(0) \approx 3$ Hz |
| Reposo: $\phi(0) \neq 0$ | Sin estímulo todas las neuronas disparan solas; con los datasets de Codex la salida sube a 28–31 Hz antes del estímulo | Tabla de abajo | `phi0`: restar $\phi(0)$ y recortar en 0 |
| $\sigma = \sqrt{v}$ (UDE) | Derivada $1/(2\sqrt v) \to \infty$ cuando la red está en silencio | 5 006 en $v = 10^{-8}$ | $\sqrt{v+1}-1$ (derivada 0.5 en 0) |
| Estímulo $I(t)$ | Salta en $t = 0.1$ y $0.6$ s | Rechazos suben de 52 a 74 si no se avisa | Pasar `tstops=[0.1, 0.6]` al integrador |
| Tasas negativas | $x_i < 0$ no tiene sentido y cambiaría el signo de la sinapsis | — | `max.(x, 0)` dentro de la ecuación |
| Grafo: distancias | Si no hay camino de $i$ a $j$, $d_{ij} = \infty$. En el dataset filtrado pasa en 5 095 pares | Promedios de distancia dan ∞ | Usar eficiencia: $1/d_{ij} = 0$ cuando no hay camino |
| Grafo: normalizar por grado | 13 neuronas del dataset filtrado quedan sin salidas: dividir por su fuerza de salida es 0/0 | 4 745 `NaN` en la matriz normalizada | Dividir por `max(salida, 1)` |
| Gráficas en escala log | $\log_{10}(0) = -\infty$: intervalos vacíos | Puntos que no se dibujan | Dibujar solo los valores que existen |

**Por qué importa la continuidad.** El teorema de existencia y unicidad (Picard–Lindelöf) garantiza una única solución si el lado derecho es Lipschitz. Con la sigmoide, $|\phi'| \le r_{max}/(4s)$, así que

$$L = \frac{1 + \frac{r_{max}}{4s}\,\kappa\,\lVert W\rVert_2}{\tau}$$

es finita: $L$ = 1 751 s⁻¹ (filtrado), 1 753 (sin filtro), 1 286 (repo). Con el escalón o con la f–I del LIF, $\phi'$ no está acotada, $L = \infty$ y el teorema no aplica. La red $g_\theta$ usa `tanh`, que es suave, así que la UDE conserva esa garantía.

**El reposo** (salida MN9 en Hz antes del estímulo, durante, y 0.6 s después de apagarlo):

| Dataset | Activación | Antes | Durante | Después |
|---|---|---|---|---|
| repo | sigmoide $\phi$ | 6.9 | 76.4 | 7.0 |
| repo | reposo en cero $\phi_0$ | 0.0 | 76.4 | 0.0 |
| filtrado | sigmoide $\phi$ | 27.7 | 76.4 | 76.4 |
| filtrado | reposo en cero $\phi_0$ | 0.0 | 76.4 | 76.4 |
| sin filtro | sigmoide $\phi$ | 30.6 | 76.3 | 76.4 |
| sin filtro | reposo en cero $\phi_0$ | 0.0 | 76.4 | 76.4 |

$\phi_0$ arregla el "antes" en los tres. El "después" **no** se arregla en los datasets de Codex: una vez encendida, la ODE se queda encendida, mientras que el LIF sí se apaga (7–10 Hz a los 0.2 s y bajando). Ver el punto 7.

En `figuras/3_continuidad.png`: las cuatro candidatas a $\phi$ (la franja roja es donde la f–I del LIF no existe), sus derivadas, la raíz con y sin arreglo, y la salida MN9 de la ODE con cada $\phi$.

## 6. Filtrado contra sin filtro

**Cerebro completo**

| | Filtrado | Sin filtro |
|---|---|---|
| Renglones del archivo | 5 342 446 | 22 285 323 |
| Pares de neuronas conectados | 3 732 460 | 19 773 733 |
| Sinapsis | 50 666 648 | 76 944 499 |
| Mínimo de sinapsis por par | 5 | 1 |
| ACh / GABA / Glu (% de sinapsis) | 59.4 / 23.5 / 15.1 | 58.9 / 22.3 / 16.3 |

El filtro deja exactamente los pares con 5 o más sinapsis: quita el 81 % de los pares y el 34 % de las sinapsis. La proporción de neurotransmisores casi no cambia.

**Subred de 365 neuronas**

| | Filtrado | Sin filtro | Tabla del repo |
|---|---|---|---|
| Conexiones | 7 916 | 22 577 | 16 905 |
| Sinapsis | 247 289 | 272 947 | 193 939 |
| Densidad | 0.060 | 0.170 | 0.127 |
| Mediana de sinapsis por conexión | 13 | 2 | 2 |
| Neuronas sin salidas | 13 | 0 | 0 |
| Mayor componente fuertemente conexa | 351 | 365 | 365 |
| Pares sin camino | 5 095 | 0 | 0 |
| Eficiencia global | 0.411 | 0.562 | 0.525 |
| Camino más corto azúcar → MN9 | 2 | 2 | 2 |

- El filtro elimina 14 661 de 22 577 conexiones (64.9 %) pero solo 25 658 de 272 947 sinapsis (9.4 %): las conexiones que quita son muchas y débiles.
- Por neurona, la pérdida de sinapsis de entrada tiene mediana 11.4 % y máximo 58.8 %.
- Estructuralmente sí cambia: 13 neuronas quedan sin salidas y 5 095 pares quedan sin camino (los puntos "no definidos" del grafo).
- La ruta principal no cambia: azúcar → MN9 sigue a 2 sinapsis.

**Actividad** (azúcar a 150 Hz, neuronas internas)

| | Filtrado | Sin filtro |
|---|---|---|
| MN9 según el LIF (Hz) | 111.3 | 115.3 |
| Tasa media según el LIF (Hz) | 52.5 | 59.8 |
| Tasa media según la ODE (Hz) | 38.6 | 42.8 |

| Diferencia por neurona (filtrado − sin filtro) | LIF | ODE |
|---|---|---|
| Correlación entre los dos datasets | 0.991 | 0.970 |
| Diferencia media (Hz) | −7.3 | −4.2 |
| Mediana de la diferencia absoluta (Hz) | 7.4 | 2.9 |
| Neuronas que cambian más de 10 Hz (de 344) | 94 | 56 |

El patrón de actividad se conserva (correlación 0.99 en el LIF) y la salida MN9 baja 3.5 %. Pero el nivel general baja unos 7 Hz por neurona y una de cada cuatro neuronas cambia más de 10 Hz. El filtro sirve para ver la estructura principal; para simular la dinámica conviene el dataset sin filtro.

**La tabla del repositorio es un tercer dataset.** No coincide con ninguno de los dos de Codex: tiene 193 939 sinapsis en la subred contra 247 289 y 272 947. Con ella el LIF da MN9 = 70.6 Hz; con los de Codex, 111–115 Hz.

## 7. Límites

- **Con los datasets de Codex la ODE no se apaga** después del estímulo y se satura en 76.4 Hz mientras el LIF llega a 115 Hz. Los parámetros ($\kappa$, $\phi$) se calibraron con la tabla del repo, que tiene entre 22 % y 29 % menos sinapsis en la subred. Para trabajar con Codex hay que recalibrar; lo primero que probaría es bajar $\kappa$ en esa proporción.
- La subred de 365 neuronas se eligió con la tabla del repo. No comprobé que siga siendo el circuito correcto con los datasets de Codex.
- La referencia es el LIF, que también es un modelo.
- La UDE del script 4 no se reentrenó con los datasets nuevos; mejora a la ODE pero se queda corta en MN9 (92 contra 111–115 Hz).

## 8. Las gráficas del borrador anterior (FlyBrainUDE)

**`00_matrices.png` y `01_grafo.png`** (tabla del repo)

| Panel | Qué representa |
|---|---|
| Matriz de adyacencia / matriz ponderada | Igual que en la sección 1 |
| "Los pesos son muy desiguales" | Histograma de sinapsis por conexión: casi todas las conexiones tienen 1–5 sinapsis, unas pocas tienen cientos |
| "Grado ≠ fuerza" | Cada punto es una neurona: cuántas conexiones salen (horizontal) contra cuántas sinapsis salen (vertical). Rojo excitatoria, azul inhibitoria. Si fueran lo mismo estarían en una línea |
| "A sola no explica la actividad" | Tasa de disparo de cada neurona contra su número de conexiones de entrada: nube sin forma |
| "W con signo sí la explica" | La misma tasa contra la entrada neta $\kappa W r$: los puntos caen sobre una curva. Esa curva es la función de activación $\phi$ real |

**`03_ode_vs_ude.png`**

| Panel                    | Qué representa                                                                                                                                                                             |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Entrenamiento            | Error del modelo en cada iteración (eje log). La UDE empieza donde termina la ODE y sigue bajando                                                                                          |
| Salida MN9 (prueba)      | Tasa de MN9 en el tiempo con un estímulo que no se usó para entrenar: LIF (negro), ODE (punteada, se pasa y no vuelve a 0), UDE (verde)                                                    |
| Todas las neuronas       | Tasa del modelo contra tasa del LIF, un punto por neurona. La ODE tiene una fila horizontal en 76 Hz (saturación); la UDE sigue la diagonal                                                |
| Función de transferencia | Puntos: tasa real de cada neurona contra su entrada media, coloreados por $\sigma$. Línea negra: $\phi$ de la ODE. Líneas de colores: lo que aprendió la UDE para tres valores de $\sigma$ |
