El estudio de los campos magnéticos se fundamenta en cinco conceptos centrales que describen desde su origen hasta su interacción con la materia y la electricidad:
## Los 5 Conceptos Centrales de los Campos Magnéticos
1. **Fuerza Magnética sobre Cargas y Corrientes:** El campo magnético (B) se define operacionalmente por la fuerza (FB​) que ejerce sobre una partícula cargada en movimiento. Esta fuerza es proporcional a la carga (q), su velocidad (v) y el campo, actuando siempre de forma perpendicular a ambos ($F_B​=qv\times B$). De igual manera, un conductor que transporta corriente experimenta una fuerza magnética en presencia de un campo externo.
2. **Fuentes del Campo Magnético (Leyes de Biot-Savart y Ampère):** Las cargas en movimiento y las corrientes eléctricas son las que inducen o crean campos magnéticos. La **Ley de Biot-Savart** permite calcular el campo producido por un elemento diferencial de corriente, mientras que la **Ley de Ampère** es una herramienta poderosa para hallar el campo en configuraciones con alta simetría, como alambres largos o solenoides
3. **Flujo Magnético y Ley de Gauss en el Magnetismo:** El flujo magnético (ΦB​) mide el número de líneas de campo que atraviesan una superficie. A diferencia del campo eléctrico, las líneas de campo magnético siempre forman espiras cerradas (no tienen principio ni fin). Por ello, la **Ley de Gauss en el magnetismo** establece que el flujo neto a través de cualquier superficie cerrada es siempre cero, lo que implica la inexistencia de monopolos magnéticos
4. **Flujo Magnético y Ley de Gauss en el Magnetismo:** El flujo magnético (ΦB​) mide el número de líneas de campo que atraviesan una superficie. A diferencia del campo eléctrico, las líneas de campo magnético siempre forman espiras cerradas (no tienen principio ni fin). Por ello, la **Ley de Gauss en el magnetismo** establece que el flujo neto a través de cualquier superficie cerrada es siempre cero.

Los imanes son muy similares a las cargas, poseen un Norte y un Sur, los opuestos se atraen, y los iguales se repelen, una diferencia es que los polos mágneticos no han sido posibles de aislar, es decir siempre y en todos los casos se encuentran en pares.
>[!note]- El polo norte geografico es realmente el polo mágnetico Sur  (esto las brujulas apuntan al sur mágnetico)

También tenemos un analogo conocido como las **líneas de campo mágnetico** estas líneas salen del polo norte, buscan alejarse y se dirijen hacía el polo sur.
![[Pasted image 20260723132434.png]]
Podemos definir la **fuerza mágnetica** como:
$$\vec{F_B}=q\vec{v}\times \vec{B}$$
Su magnitud se define como:$$F_b = |q||v||b|\sin(\theta)$$
>[!Abstract]- La mano Derecha tiene dos formas de verse 
>1. El dedo indice apuntara en la dirección del primer vector que aparece en la operación del producto escalar, el dedo medio apuntara en la dirección del segundo vector y el dedo pulgar dara como resultado la d irecicón del producto cruz (no olvide que la carga influye en la dirección)
>2. Su dedo pulgar indicara la dirección del primer vector, donde apunten sus dedos sera la dirección del segundo y como resultado su palma dira la dirección en la que se establece la fuerza (note que se puede visualizar como hacía donde tiene que empujar).


Estas dos definiciones son la mismas que las de un producto punto clásico, note que si no hay movimiento de la #carga (no hay *velocidad*), esto implica que no hay campo magnético generado.
el valor mínimo de la fuerza (0) se dara cuando $\theta= 0, \pi$ note que se maximiza cuando el producto cruz es mayor ($\theta = \pi/2$ gracias al $\sin(\theta)$)
Hay diferencias entre la fuerza eléctrica (Ley de Coulumb) y la Fuerza Mágnetica?
- El vector fuerza eléctrica actúa a lo largo de la dirección del campo eléctrico (los unía una linea), el vector de fuerza #magnética es perpendicular al campo magnético (por el producto cruz).
- la fuerza eléctrica solo necesita una carga (no necesita estar en movimiento), la fuerza magnética necesita ***velocidad*** (movimiento)
- La fuerza eléctrica efectúa trabajo al desplazar una partícula con carga, en tanto que la fuerza magnética asociada con un campo magnético estable no efectúa trabajo cuando se desplaza una partícula, debido a que la fuerza es perpendicular al desplazamiento $W=Fd\cos{\theta}$
Con base en este último enunciado y también con el teorema trabajo-energía ci- nética, se concluye que la energía cinética de una partícula con carga que se mueve a través de un campo magnético no puede ser modificada por el campo magnético solo.

>[!important]- El campo magnético, puede modificar la dirección del vector velocidad pero no puede cambiar la rapidez ni la energía cinética de la partícula.

## Unidad del SI
$$1T = 1\dfrac{N}{C\cdot m/s}$$
$$1T = 10^4 G$$
>[!Example]- Recuerde que la fuerza de una carga negativa siempre es **antiparalela** a una fuerza de una carga positiva

## Movimiento de una particula con carga en un campo magnético uniforme
Imagine que el campo magnético esta entrando a la pagina del libro, la velocidad es perpendicular al mismo, esta se movera siguiendo uan trayectoria, siendo un MCU (Movimiento Circular Uniforme).
Ya con esto podemos utilizar las formulas de Física I (recuerde que el angulo entre $v$ y $B$ es de 90°)
$$F_B = ma \rightarrow qvB = m\frac{v^2}{r}$$
Después de haber aplicado la aceleración centripeta puede encontrar el radio el cual va a depender en mayoria de la velocidad de la particula (como clásico en los MCU), la velocidad angular la cual no depende la velocidad de la particula, sino del campo magnetico, la carga y la masa y finalmente el periodo de la misma particula.
[Página del Libro](Serway.pdf.md#page=204)


>[!Tip] En los ejercicios los siguientes enunciados pueden facilitar ciertos valores
>Ejemplo: **Electron**, ya nos dan el valor de la **carga** y el valor de la **masa** implicitamente (igual para un positron o un proton).
>Así mismo con algunas ideas geometricas (cuando los vectores son perpendicular su angulos es 90°)
>Masa de un electron = $9.11\times 10^{-31}$
>Masa de un proton = $1.67\times 10^{-27}$
>carga de un proton y un electron (cambia el signo) = $1.60 \times 10^{-19}$
>El voltaje tambien puede influir en la velocidad de los electrones (afectando su comportamiento aunque el campo magnetico sea igual) realice balances de energía sencillos


Cuando las partículas con carga se mueven en un campo magnético no uniforme, su movimiento es complejo. Por ejemplo, en un campo magnético intenso en sus ex- tremos y débil en su parte media, como el que se muestra en la figura 29.10, las partículas pueden oscilar entre dos posiciones. Una partícula con carga sale de un extremo de la espiral a lo largo de las líneas de campo hasta llegar al otro extremo, donde in- vierte su trayectoria y de regreso en la espiral. Este esquema se conoce como botella mag- nética, ya que las partículas con carga pueden quedar atrapadas en su interior. Se ha utilizado esta botella magnética para confinar plasma, un gas formado por iones y elec- trones. Este esquema de confinamiento de plasma podría jugar un papel crucial en el control de la fusión nuclear, proceso que podría suministrar en el futuro una fuente de energía casi infinita. Por desgracia, la botella magnética tiene sus problemas. Si un gran número de partículas está atrapado, las colisiones que se presentan entre ellas hacen que fi nalmente se fuguen del sistema.
## 29.3 Aplicaciones
Estos casos son ideales, donde solo el campo magnético aplica, ahora consideremos la fuerza total si un campo electrico se agrega:
$$ \vec F= q\vec E + q \vec v \times \vec B$$
esta se conoce como la fuerza de **Lorentz**
En muchos experimentos que incluyen partículas con carga en movimiento, es impor- tante que todas las partículas se muevan a la misma velocidad, esto se puede lograr apli- cando la combinación de un campo eléctrico con uno magnético orientados como se ilustra en la figura 29.12.
la partícula con carga se modela como una partícula en equilibrio y se mueve en línea recta vertical a través de la región de los campos. (Fuerza = 0) pruebe el despeje.
Sólo aquellas partículas que tengan esta rapidez pasarán sin desviarse a través de los campos eléctrico y magnético mutuamente perpendiculares. La fuerza magnética que se ejerce sobre partículas que se mueven con magnitudes de velocidad más elevadas es mayor a la fuerza eléctrica, lo que desvía las partículas hacia la izquierda. Las que se muevan con magnitudes de velocidad menores se desviarán hacia la derecha.
Ejemplos como estos pueden concluir a balances de energía donde se hace uso de que ambas fuerzas al llegar a un equilibrio se anulan y resultan en la expresión:
$$v=\dfrac{E}{B}$$
imagine las posibilidades de manipular cargas utilizando sistemas de campos magneticos donde el campo apunta en una dirección conveniente y luego se combina con el radio del MCU que generan las particulas.
## 29.4 Conductor que Transporta Corriente
Hasta el momento hemos realizado estos procedimientos con unas cuantas cargas, pero recordemos la definición de [[5. Corriente (Conceptos de Circuitos)#Corriente (I)|Corriente]] que son una cantidad de cargas dadas moviendose en un conductor, un experimento sencillo donde se pone un alambre de forma perpendicular a un iman en forma de C puede dar 3 resultados posibles.
>[!check] 1. Quedarse estatico cuando $I=0$
>2. Cuando la corriente conduce hacía arriba del alambre se ira a la derecha (note que por la regla de la mano derecha la fuerza apunta en la misma dirección).
>3. Resultado opuesto a **2.**

para encontrar la fuerza en el alambre, multiplique la fuerza magnética sobre una carga por el número de cargas en el segmento. $nAL$  donde $AL$ es el volumen del alambre ($A$ area transversal y $L$ longitud del alambre, $n$ representa la cantidad de cargas por unidad de volumen), como resultado obtiene:
$$\vec{F}=(q\vec{v}\times\vec{B})nAL$$
la corriente en un alambre es $I=nqv_dA$ y la ecuación anterior se visualiza como:
$$\vec{F}=I\vec{L}\times\vec{B}$$
donde $\vec{L}$ define la dirección de la corriente $I$ y su magnitud es igual a la longitud del segmento $L$.
Ahora imagine que doblamos ese iman en una figura a convenir, podemos visualiza, mientras su seccion transversal sea uniforme, se puede integrar la ecuación y quedaría definida de la siguien forma.
$$\vec{F}=I\int_a^bd\vec{s}\times \vec{B}$$
puede separar la integral en más integral aprovechando la simetría y visualizando los casos donde el producto cruz **maximice** o **minimice** su valor siendo perpendicular o paralelo respectivamente.



Tags: #carga #electrico #magnética
