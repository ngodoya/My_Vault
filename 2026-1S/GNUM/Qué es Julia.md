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
Tags: #Tipado_Dinámico #python #Numpy #C #Linux #JupyterLab