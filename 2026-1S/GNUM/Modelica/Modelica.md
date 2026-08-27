# Para Qué Este Repositorio?
La idea del presente repositorio busca responder una pregunta en concreto:
**Cómo puede ser usado Modelica como un lenguaje computacional para modelación matemática, simulación y experimentación númerica en Ingeniería**
Se busca que todo lo que se realice en este repositorio sea reproducible para el aprendizaje de los estudiantes en el Lenguaje de Modelica, pero más importante, en el razonamiento y comprensión del Lenguaje, limitaciones, casos de uso, ejemplos, proyectos o incluso como aplicarlo en las diversas áreas de la ingeniería.
## Qué es Modelica?
Modelica es un lenguaje compilado para modelado de sistemas **ciber-fisicos** (Union de sistemas físicos con programas de computación y redes, las redes se utilizan para enviar datos y información del problema), el lenguaje es de uso libre y gratuito, esta a cargo de la asociación **Modelica**, además de ser un lenguaje de ***código abierto*** . Utilizado por los siguientes softwares de Modelación:
- **Dassault Systemes Dymola:** Enfocado al entorno integral de modelado y simulación en sistemas complejos y multidisciplinarios. 
- **Modelon Impact:** Plataforma en la nube la cual cuenta con conexiones nativas e integraciones con  herramientas como Python, Microsoft Excel y Jupyter Notebooks mediante APIs
- **Wolfram System Modeller:** Tiene una ventaja frente al analisis de sistemas físicos multidimensionales, es una ventaja ya que permite elaborar tareas y trabajos de varias áreas al mismo tiempo.
- **OpenModelica:** Entorno de código abierto (open-source) enfocado en la investigación y educación, que destaca por su flexibilidad para el desarrollo, prueba y simulación gratuita de librerías multidominio sin restricciones de licenciamiento.
## Características
- **Acausal:** Las ecuaciones se escriben de la misma forma que aparecen en los libros de texto.
	Ejemplo: $$\dfrac{d^2 y}{dt^2}-\dfrac{d y}{d t}=y-x$$
	No hay una necesidad de despejar la variable. Esto produce **conectores que no van de entrada ni de salida**, los datos describen como se unen las ideas físicas de la ecuación y su resolución. No estamos atados a dar y recibir una variable específica, cómo escribimos la ecuación exactamente como la teníamos en el libro, está funciona como un conector sin dirección definida.

>[!python]- Diferencias con un Lenguaje Causal (imperativo)
> En un lenguaje Imperativo sería necesario despejar la derivada de mayor ordén, o incluso generar un sistema de ecuaciones diferenciales ordinarias y empezar a solucionar por un método iterativo

- **Multi-dominio:** Al ser un lenguaje pensado para resolver sistemas de ecuaciones diferenciales, cualquier campo de la física puede ser modelado, por lo tanto varios pueden simularse al mismo tiempo.
- **Jerárquico:** Es un lenguaje **orientado a objetos** donde la *encapsulación* y *herencia* juegan un papel clave en la construcción de modelos. Esto permite descomponer problemas masivos con una complejidad avanzada y convertirlos en problemas con componentes más simples conectados entre sí.
- **Visual:** El código fuente define la forma de visualizar el diagrama del sistema y los iconos de los componentes, lo que permite utilizar un montón de funciones sin necesidad de conocer mucho sobre el uso del código fuente.
- **Híbrido:** es posible modelar sistemas de ecuaciones continuas en el tiempo y eventos. Eventos en los que otro sistema de ecuaciones puede entrar en funcionamiento para modelizar lo que está sucediendo.
- **Documentado:** EL código fuente y los modelos pueden ser fuertemente documentados, desde un manual en HTML, hasta documentar variables y ecuaciones, lo cual permite leer el modelo de una forma sencilla.


### Paradigmas
Cómo ya vimos previamente el lenguaje cumple con los siguientes paradigmas.
1. **Paradigma Declarativo (Ecuacional)**
2. **Orientado a Objetos (POO)**
3. **Paradigma Acausal**
4. **Paradigma Imperativo (Algoritmos):** Aunque el lenguaje no nació para ello, el mismo incluyo secciones especiales conocidas como `algorithm`. Dentro de las secciones el código es secuencial, paso a paso
5. **Paradigma de Eventos:** Utiliza cláusulas como `when` para manejar cambios bruscos de estado o señales de control digital


---
## Modelación Matemática 
### Cómo transformamos un sistema físico en ecuaciones
### Cómo Representa Modelica las Ecuaciones Diferenciales
### Qué pasa cuando el modelo tiene ecuaciones algebraicas?
---
## Ingeniería
### Sistemas Mecánicos
### Sistemas Eléctricos
### Sistemas Termicos
### Sistemas de Fluidos
### Sistemas de Manufactura
---
Aunque mi proposito con el repositorio no es buscar un lenguaje que reemplace a Python o a Julia (porque los 3 lenguajes no están ni cerca de haber sido creado con el mismo proposito), si busco encontrar una conexión entre las áreas que pueden abarcar los lenguajes previamente mencionados, una de las maneras en que se puede ejecutar esto, es utilizando Modelica como le software de **Modelado** y/o **Simulación** y Python o Julia se convierten en la capa de post-procesamiento, análisis o incluso optimización de nuestro modelo.
Este repositorio estudía Modelica desde dos ámbitos diferentes, Modelica como lenguaje y #OpenModelica como software, es importante conocer el manejo y abstracción que utiliza el lenguaje, debido a que se rige por el principio de la programación orientada a objetos (POO), el software de OpenModelica busca sintetizar y abstraer la idea del lenguaje, sus clases, su herencia, el manejo de ecuaciones, librerías, componentes, bloques y utilizarlo en la simulación, donde ya ocurre el respectivo análisis, Optimización o incluso lo me´todos númericos que se aplican.
# Entorno: Windows / Linux / WSL
En el siguiente [Enlace](https://openmodelica.org/) puede encontrar la página oficial de #OpenModelica, puede encontrar la lista de herramientas proporcionadas por OpenModelica en la misma página, para ello debe dirigirse al apartado  Users -> Tools, donde puede encontrar las siguientes herramientas:
- **Advanced Interactive OpenModelica Compiler (OMC):** Trae un compilador que convierte el código Fuente (Modelica) a código #C para la respectiva simulación.
- **Interactive OpenModelica Shell** Interfaz interactiva de comandos, escribes una orden o expresión, presionas Enter, el sistema la procesa al instante y te devuelve una respuesta en la línea siguiente. Similar a la terminal de comando de #Python, esto se debe a que Modelica es un lenguaje interpretado.
- **OpenModelica Notebook (OMNotebook)**: Libro de texto mediante ejercicios del lenguaje Modelica, similar a los cuadernillos de Notebook.
- **OMEdit:** Programa principal donde realizaremos los modelos y donde se va a programar en Modelica.
- **OMEdit Integrated with Electronic Notebooks and Interactive Simulation:** OMEdit para simulación iterativa, para formación.
- **OMPython:** Permite utilizar el lenguaje de Modelica en el entorno de Python, util para evitar exportar datos.
El resto de herramientas se iran estudiando en el transcurso del tiempo, pero estás son las más relevantes.

## OpenModelica en Windows

### Instalación Windows
En el apartado [Download](https://openmodelica.org/download/download-windows/) puede visualizar la instalación para Windows, también está para Linux, Mac, Maquinas Virtuales e incluso otros sistemas operativos, por el momento el enfoque será en el Sistema Operativo de Windows y Linux, en el mismo apartado se pueden ver distintas versiones del sistema, es recomendable instalar la versión **Oficial Release** debido a que ya tiene todas las carácteristicas se encuentran validadas.
A fecha de hoy el sistema se encuentra en su versión 1.27, la cual solo esta disponible para 64 Bits (teniendo en cuenta el avance en la memoria RAM y la exigencía del mercado actual), el archivo a descargar será el conocido con el nombre: `OpenModelica-v1.**.0-64bit.exe` donde ``**`` corresponde a la última versión disponible del sistema. Una vez descargado el archivo .exe se procede con su instalación.
Puede que salten algunas alertas de seguridad desde #Windows, para casos como estos ignore las alertas de seguridad, sobre todo en las últimas versiones Windows su protección está más cerca de ser un virus que un propio antivirus.
## OpenModelica en Linux
### Instalación en Linux
La instalación oficial se puede encontrar en el siguiente [Enlace](https://openmodelica.org/download/download-linux/).

Cómo muchas de las aplicaciones en los sistemas operativos #Linux su instalación se remite a solo unas líneas en la terminal de nuestra distribución, en este caso #OpenModelica solo esta disponible para distribuciones como Debian o Ubuntu, siendo la versión de Ubuntu la que ha recibido mayor apoyo y seguimiento en sus versiones, si desea visualizar el [historial de commits](https://github.com/OpenModelica/OpenModelica/commits/v1.27.0) puede hacerlo en el enlace anterior, donde podrá visualizar la información del repositorio oficial de OpenModelica.
La instalación se remite a simplemente escribir los siguientes comandos para actualizar los paquetes y instalar la firma digital certificada para los paquetes oficiales de OpenModelica:
```bash
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
curl -fsSL https://build.openmodelica.org/apt/openmodelica.asc | \
  sudo gpg --dearmor -o /usr/share/keyrings/openmodelica-keyring.gpg
```
En este apartado será relevante conocer la arquitectura de su CPU, su OS (sistema operativo) y la rama de lanzamiento que desea utilizar, una vez tenga esta información puede llenar los siguientes atributos en la página de descargas de OpenModelica, se debería de visualizar un código similar al siguiente *(noté que es distinto dependieno de sus necesidades)*.
Comandos para Conocer la arquitectura de su CPU y el OS de su distribución:
```bash
sudo nano /etc/apt/sources.list # Arquitectura de CPU
cat /etc/os-release #OS
```
una vez que ingreso lo necesario visualizará un código similar al siguiente:
![[Modelica Cpu_arch.png]]
Luego puede instalar OpenModelica de la siguiente manera:
```bash
sudo apt update
sudo apt install openmodelica
```
Si desea instalar una versión con el mismo proposito pero evitando instalar gráficos, puede realizarlo con el siguiente comando, el cual obviara algunos paquetes, no cambiará el funcionamiento del software, simplemente instalara una versión *minimalista* del mismo.
```bash
sudo apt install --no-install-recommends omc
```
## Librerias en Modelica
Existe un gestor de paquetes para las librerias de Modelica construido en la secuencia de comandos y la interfaz gráfica del #OMEdit, si desea conocer más sobre ello, puede remitirse a la siguiente [documentación](https://openmodelica.org/doc/OpenModelicaUsersGuide/latest/packagemanager.html) para más detalles.
### Instalación Offline
para realizar el siguiente comando no es necesario utilizar internet, sin el mismo sigue siendo posible instalar la libreria estandar de Modelica.
```bash
sudo apt install omlibrary
```
Estás Librerías serán instaladas automaticamente por the gestor de paquetes en el directorio donde el usuario instaló OpenModelica, tan pronto como cualquier herramienta de OpenModelica intente carga cualquier librería del sistema por primera vez, un ejemplo puede ser #OMEdit 
## IDE: Cómo Utilizar
Para utilizar el Lenguaje de Modelica existen muchos entornos para hacer uso del lenguaje, entre ellos se encuentran los siguientes:
- #VsCode: Para utilizar el lenguaje se puede instalar utilizando las siguientes extensiones: **Modelica** (de SimplyDanny), **ModelScript** (permite edición de diagramas y simulación), o el **Modelica Language Server** (Oficial de #OpenModelica)
# Qué hace único a Modelica?
Más allá de la syntax de Modelica lo importante es resolver la pregunta de, *Qué se esconde detrás del Código*, qué fenomeno físico se busca explicar y desarrollar
Tags: #VsCode #OpenModelica #C #Windows #Linux