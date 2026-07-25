# Matplotlib
Una libreria que nace para desplazar a las toolboxs de matlab, tiene varias formas de modificar graficas, decorar con colores, formas o incluso tipos de lineas en python
## Método orientado a objetos

A continuación realizaremos una introducción al método orientado a objetos de Matplotlib.

La lógica consiste en  crear objetos de la clase Figura y luego emplear métodos o atributos de ese objeto. Este enfoque es más práctico cuando se trata de un canvas que tiene múltiples gráficos en él.

Para comenzar, creamos una instancia de figura, posteriormente se agregan los ejes a esa figura, los ejes se adicionan con la función add_axes(), la cual recibe como parametros valores entre cero y uno en notación decimal que representan en forma porcentual la posición de los ejes (izquierda, abajo), y las dimensiones de estos (ancho, alto):
```python
fig = plt.figure()   #Creamos una Figura (canvas vacío)
ejes = fig.add_axes([0.5, 0.5, 1, 1])   #añadimos dimensiones de los ejes
ejes.plot(x, y, 'b')     # 'b' hace referencia al color azul (blue)
ejes.set_xlabel('Eje X') # Nótese el uso de "set_" al principio del nombre de los métodos
ejes.set_ylabel('Eje Y')
ejes.set_title('Título de la Figura')
fig.show()
```
>[!python] Aunque en principio el código puede parecer un poco más complicado, el método orientado a objetos tiene mayores ventajas que el método convencional, ya que permite mas control sobre la diagramación, por ejemplo se tiene mas control sobre el manejo y ubicación de los ejes, pudiendo entre otras cosas trabajar con mas de un par de ejes sobre una misma gráfica como se muestra en el siguiente ejemplo:
>```python
>axes1 = fig.add_axes([0.2, 0.2, 0.8, 0.8]) # eje principal
axes2 = fig.add_axes([0.5, 0.5, 0.2, 0.2]) # eje interior
add_axes([x_inicial, y_inicial, ancho, largo])```
### subplots()

El método plt.subplots() sirve como gestor automático de gráficos, de esta manera se pueden crear mas de una gŕafica sobre un mismo canvas o instancia de figure. El método retorna una instancia de tipo figura y un arreglo de ejes que referencia a cada una de las gŕaficas.

Casos de uso básicos:
- ```python
# Canvas vacío de 2x4 subplots
	fig, axes = plt.subplots(nrows=2, ncols=4)
	axes[1,1].plot(x, y, 'b')
	fig.tight_layout()   #para evitar superposición de elementos
```
```python
for fila in axes:                   #Acceso mediante la iteración de sus elementos
  for eje in fila:
    eje.plot(x, y, 'b')
    eje.set_xlabel('x')
    eje.set_ylabel('y')
    eje.set_title('title')

axes[1][2].clear()
axes[1][2].plot(y, x, 'r')          #Acceso mediante uso de sus indices

# Para mostrar la figura
fig.tight_layout()
fig
```
## Tamaño de figuras y DPI (Dots per Inch)

#Matplotlib permite especificar el DPI y el tamaño de la figura cuando se crea el objeto Figure. Para esto, se usan los argumentos de las palabras clave `figsize` y `dpi`.
* `figsize` es una tupla del ancho y alto de la figura en pulgadas
* `dpi` es la cantidad de puntos por pulgada (pixel por pulgada).

Por ejemplo:
```python
fig = plt.figure(figsize=(3,3))

ax = fig.add_axes([0,0,1,1])
ax.plot(x,y)
```

____

## Leyendas, etiquetas, títulos
### Títulos de Figuras

Use el método `set_title` en el objeto `axes`
### Etiquetas de ejes

Los métodos `set_xlabel` y `set_ylabel` permiten asignar nombres a los ejes
### Leyenda
Se puede usar el parámetro **label="texto leyenda"** cuando se añaden plots u otros objetos a la Figura. Después, se llama al método **legend** para incluir la leyenda en el gráfico:
```python
fig = plt.figure()

ax = fig.add_axes([0,0.3,1,1])

ax.plot(x, x**2, label="$x^2$")
ax.plot(x, x**3, label="$x^3$")
ax.legend()
```
El método **legend** tiene un parámetro opcional **loc** que se usa para especificar la posición de la leyenda en la Figura. Soporta códigos númericos o la cadena directamente. Ver la documentación para conocer muchas más opciones: http://matplotlib.org/users/legend_guide.html#legend-location.
```python
#ax.legend(loc=1) # upper right
#ax.legend(loc=2) # upper left
#ax.legend(loc=3) # lower left
#ax.legend(loc=4) # lower right

# Más común
#ax.legend(loc=0) # matplotlib decide la mejor posición

# Personalizado
ax.legend(loc=(0.5,0.8))

fig

```
## Colores, ancho de líneas y tipo de líneas

Matplotlib ofrece *muchas* opciones para personalizar los colores, ancho de líneas y tipo de líneas.

Matplotlib soporta una sintaxis básica similar a MatLab que sugerimos evitar en aras de la claridad:
### Sintaxis similar a MatLab
Con matplotlib, podemos definir los colores de las líneas y otros elementos gráficos de varias maneras. En primer lugar, podemos usar la sintaxis similar a MATLAB donde `'b'` significa azul, `'g'` significa verde, etc. También se pueden seleccionar estilos de línea: donde, por ejemplo, 'b.-' significa una línea azul con puntos:
```python
# Estilo MATLAB
fig, ax = plt.subplots()
ax.plot(x, x**2, 'b.--') # línea azul (b) con puntos
ax.plot(x, x**3, 'g--') # línea punteada verde (g)
```
### Colores usando el parámetro `color=`
Podemos definir colores por sus nombres o códigos hexadecimales RGB y, opcionalmente, proporcionar un valor alfa utilizando los argumentos de palabras clave `color` y `alfa`. Alpha indica opacidad.
```python
fig, ax = plt.subplots()

ax.plot(x, x+1, color="blue", alpha=0.1) # medio-transparente (alpha=0.5)
ax.plot(x, x+2, color=(0.1,0.2,0.5,0.5)) # Código hexadecimal RGB (RGB Hex Code)
ax.plot(x, x+3, color="#FF8F09")         # Código hexadecimal RGB
```
### Estilos de líneas y marcadores
Para cambiar el ancho de línea se utiliza el parámetro `linewidth` (o simplemente `lw`). El estilo de línea se puede selecionar mediante el argumento `linestyle` (o `ls`):
```python
fig, ax = plt.subplots(figsize=(12,6))

# linewidth
ax.plot(x, x+1, color="red", linewidth=0.25)
ax.plot(x, x+2, color="red", linewidth=0.50)
ax.plot(x, x+3, color="red", linewidth=1.00)
ax.plot(x, x+4, color="red", linewidth=2.00)

# linestyle: ‘-‘, ‘-.’, ‘:’, ‘steps’
ax.plot(x, x+5, color="green", lw=3, linestyle='-')
ax.plot(x, x+6, color="green", lw=3, ls='-.')
ax.plot(x, x+7, color="green", lw=3, ls=':')

# línea personalizada
line, = ax.plot(x, x+8, color="black", lw=1.50)
line.set_dashes([5, 2, 15, 10]) # formato: longitud de línea, longitud de espacio, ...

# marcadores: marker = '+', 'o', '*', 's', ',', '.', '1', '2', '3', '4', ...
ax.plot(x, x+ 9, color="blue", lw=0.5, ls='-', marker='+')
ax.plot(x, x+10, color="blue", lw=2, ls='--', marker='o')
ax.plot(x, x+11, color="blue", lw=2, ls='-', marker='s')
ax.plot(x, x+12, color="blue", lw=2, ls='--', marker='1')

# tamaño y color del marcador
ax.plot(x, x+13, color="purple", lw=1, ls='-', marker='o', markersize=2)
ax.plot(x, x+14, color="purple", lw=1, ls='-', marker='o', markersize=4)
ax.plot(x, x+15, color="purple", lw=1, ls='-', marker='o', markersize=8, markerfacecolor="red")
ax.plot(x, x+16, color="purple", lw=1, ls='-', marker='s', markersize=8,
        markerfacecolor="yellow", markeredgewidth=3, markeredgecolor="green");

```

>[!Example] Ejercicio
>Graficar $y = x^5 + 3$ varias veces, desplanzando la curva en el eje x. Modifique de cada línea, color, ancho de línea y estilo de línea.
## Ejes

### Rango

Podemos configurar los rangos de los ejes usando los métodos `set_ylim` y `set_xlim` del objeto del eje, o llamando al método `axis ('tight')` para obtener automáticamente rangos de ejes "ajustados":
```python
fig, axes = plt.subplots(1, 3, figsize=(12, 4))

axes[0].plot(x, x**2) # Se puede graficar sobre la misma figura llamando varias veces a plot()
axes[0].plot(x, x**3)
axes[0].set_title("Rango de ejes por defecto")

axes[1].plot(x, x**2, x, x**3) # Se puede hacer esto en una sola línea
#axes[1].axis('tight')
axes[1].autoscale(enable=True, axis='both', tight=True) #axis : ['both' | 'x' | 'y']; default is 'both'
axes[1].set_title("Rango ajustado")

axes[2].plot(x, x**2, x, x**3)
axes[2].set_ylim([0, 10])
axes[2].set_xlim([2, 3])
axes[2].set_title("Rango personalizado");
```
## Tipos de gráficos especiales

Al igual que con Pandas, en Matplotlib se pueden crear varios tipos de gráficos: barplots, histogramas, scatter plots, y muchos más. La mayoría de estos gráficos los crearemos usando Seaborn, una librería para gráficos estadísticos para Python. Pero aquí se presentan algunos ejemplos con matplotlib:
La forma de uso de estas funciones, es similar al de la función plot, se envían como argumentos básicos los datos a graficar contenidos en dos arreglos, y es posible la personalización de algunas propiedades del gráfico de acuerdo con el tipo de gráfico que se este usando mediante el envío de parametros opcionales.
### scatter()

En el ejemplo siguiente se usa la función scatter, con esta se grafican los datos de una manera despersa como se ve en el resultado, adicionalmente permite uso de algunos modificadores como el caso de ''marker' para definir la representación de los puntos en la gráfica,
### hist()

Esta función permite la diagramación de los datos con estilo tipo histograma, en donde los datos son representados por barras verticales a lo largo del eje x, en el ejemplo siguiente se ilustra su uso para lo cual se generan previamente los arrays con los datos a diagramar.

El parametro bins define la cantidad de barras para el diagrama, este puede ser un valor númerico, un rango, o una cadena. (para el caso de una cadena, esta debe correponder a uno de los valores preestablecidos de acuerdo, los cuales puede consultar en la documentación en donde también se detallan los parámetros que acepta esta función https://matplotlib.org/api/_as_gen/matplotlib.pyplot.hist.html )
```python
from random import sample
data = sample(range(1, 100), 50)  #De esta forma se genera un arreglo de 50 elementos con valores aleatorios comprendidos entre 1 y 100
plt.hist(data, bins=10, width=5)   #bins define el número de barras (10 por defecto)
```
### boxplot()

Mediante esta función se gráfican los datos en un diagrama de cajas, para el ejemplo siguiente se grafican los diagramas de caja de tres arreglos generados aleatoriamente con desviación estandar de 1, 2 y 3 respectivamente:
```python
data = [np.random.normal(0, std, 100) for std in range(1, 4)] #contendrá 3 arreglos de 100 elementos cada uno, con valores aleatorios de distribución normal
#con desviación estandar variando entre 1 y 3
# boxplot rectangular
plt.boxplot(data,vert=True,patch_artist=True)
plt.show()

```
## Lecturas adicionales

Los siguientes enlaces corresponden a sitios en donde encontrará información muy útil para profundizar en el conocimiento de las funcionalides de la libreria Matplotlib:
* http://www.matplotlib.org
* http://matplotlib.org/gallery.html - Ejemplos - **muy recomendado.**
* http://www.labri.fr/perso/nrougier/teaching/matplotlib/ - Excelente tutorial.
* http://scipy-lectures.github.io/matplotlib/matplotlib.html


Tags: #Numpy #Matplotlib 