# Para Qué Este Repositorio?
La idea del presente repositorio busca responder una pregunta en concreto:
**Cómo puede ser usado Modelica como un lenguaje computacional para modelación matemática, simulación y experimentación númerica en Ingeniería**
Se busca que todo lo que se realice en este repositorio sea reproducible para el aprendizaje de los estudiantes en el Lenguaje de Modelica, pero más importante, en el razonamiento y comprensión del Lenguaje, limitaciones, casos de uso, ejemplos, proyectos o incluso como aplicarlo en las diversas áreas de la ingeniería.
## Qué es Modelica?
### Es orientado a Objetos?
### Es Declarativo o Imperativo?
### Esta basado en Ecuaciones?
### Es multiparadigma?
### Que es un `model`, `block`, `function`, `package`, etc.?

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
Cómo muchas de las aplicaciones en los sistemas operativos #Linux su instalación se remite a solo unas líneas en la terminal de nuestra distribución, en este caso #OpenModelica solo esta disponible para distribuciones como Debian o Ubuntu, siendo la versión de Ubuntu la que ha recibido mayor apoyo y seguimiento en sus versiones, si desea visualizar 
## IDE: Cómo Utilizar
Para utilizar el Lenguaje de Modelica existen muchos entornos para hacer uso del lenguaje, entre ellos se encuentran los siguientes:
- #VsCode: Para utilizar el lenguaje se puede instalar utilizando las siguientes extensiones: **Modelica** (de SimplyDanny), **ModelScript** (permite edición de diagramas y simulación), o el **Modelica Language Server** (Oficial de #OpenModelica)
# Qué hace único a Modelica?
Más allá de la syntax de Modelica lo importante es resolver la pregunta de, *Qué se esconde detrás del Código*, qué fenomeno físico se busca explicar y desarrollar
Tags: #VsCode #OpenModelica #C #Windows #Linux