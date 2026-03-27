# Cómo subo mis avances?
>[!Tip]
Dejo una syntax de comandos  básicos para trabajar con Github, estos comandos se usan en la terminal de su entorno virtual (Recomiendo usar **VS Code**), cómo instalarlo? [Aquí](https://code.visualstudio.com/download)

Github es una herramienta muy poderosa para el trabajo en equipo, más allá de los comandos que voy a anotar para enviar, recoger y comentar cambios, tiene mucho potencial para incluso revisar y administrar que cambios se suben al proyecto final.

Para utilizar Github en Windows (Aunque lo recomendable es que utilice Linux) instale Git.

## Qué es Git??
Es un versionador de documentos de texto, permite almacenar cambios, revisar versiones pasadas, analizar modificaciones entre muchas otras funciones. Para instalar solo basta descargar este [enlace](https://github.com/git-for-windows/git/releases/download/v2.39.1.windows.1/Git-2.39.1-64-bit.exe). La ventaja es que viene integrado con una consola estilo unix. 

## Comando para la Consola y guardar cambios.

```bash
# Traer un repositorio
git clone https://github.com/nombre_usuario/repo.git
# Subir Cambios
git add.
git commit -m'Qué Cambio se realizo' 
git push
# Traer Cambios
git pull
```
Estos son los 3 comandos más básicos para trabajar en un repositorio (así se conoce a los ***Portafolios*** de GitHub).
- *git clone https://github.com/nombre_usuario/repo.git* Este comando se utiliza para descar los archivos de la nube de GitHub a su entorno personal (solo es necesario usarlo una vez, ya despues utilizaremos git pull para actualizar con los archivos de la nube).

>[!Example]
git clone https://github.com/ngodoya/Semillero_Hidrogeno_Verde.git

- *git add .* se utiliza para guardar los cambios que se han hecho en los respectivos archivos, usualmente se utiliza *git add .* para hacer el guardado en **TODOS** los archivos, lo más responsable sería utilizar *git add nombre_archivo.py.* el py es un ejemplo del tipo de archivo que quiere guardar.
- *git commit -m"Qué cambio se realizo"* los git commit se utilizan mucho a la hora de hacer registros en la rama de desarrollo de proyecto, suelen ser sencillos y directos con los cambios y avances que se realizaron.
Después de hacer un Git add . se puede hacer sin necesidad de la terminal en Visual yendo a la siguiente área.
![Commit Desde VS Code](assets/Commit_VS_Code.png)
Note que también Visual Code muestra que archivos se crearon, se actualizaron y se borraron, además de tener una rama de desarrollo.
- *git push* Básicamente una forma de mandar lo que yo trabaje en mi entorno (computador personal) a la nube de github y que otras personas tengan acceso a esos cambios.
- *git pull* Una forma de traer los cambios realizados por otros integrantes y que ya se *pushearon* (o sea que ya usaron el comando de git push)

# Podemos Trabajar en LaTex al tiempo? 
Claro que sí!!!, desde **VS Code** hay alternativas a utilizar Overleaf y que no colapsan si el archivo .tex a imprimir se sobrecarga, evitando tener que pagar una licencia.
## Qué necesitamos??
Es relevante detonar que necesitamos de una extensión para visualizar el codigo .tex que estemos haciendo, en palabras mas simples ver el pdf que vamos a imprimir.
Para ello recomiendo el siguiente [Tutorial](https://www.youtube.com/watch?v=Mty0vHb0knI). 

- Extensiones a usar:
[LaTeX  Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)

Para un Tutorial más avanzado de como realizar textos cientificos con las herramientas dadas remitase al siguiente [Link](https://www.youtube.com/watch?v=vIImoKpKWIo)

Si desea visualizar un ejemplo de un archivo tex en este respositorio, remitase a este [Documento](Latex/Articulo.tex)