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

Tags: #Numpy #Matplotlib 