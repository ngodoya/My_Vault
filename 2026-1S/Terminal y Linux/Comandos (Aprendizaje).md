# Cómo abrir Jupyter-Notebook en Conda?

```bash
conda activate __(Nombre Entorno)__ 
# Si no recuerda el entorno utilice el comando
conda info --env
## Active la ruta que desea
conda activate UNAL_Data
### Saldra algo así
(UNAL_Data) nick1604@Nick-Desktop:~$ 
# debe digitar
anaconda-navigator

```

# Acciones usuales

```bash
ls #(Ubicarse)
mkdir #Mover (archivos)
rmdir #Eliminar(archivo dentro de la carpeta que estes)
cd #Acceder a la carpeta en terminal
pwd #conocer donde estar (ruta)
```

# Crear entornos

```bash
# Terminal crea el entorno
python3.14 -m venv nombre
source nombre/bin/activate
pip install (librerias) (librerias) #(note que no necesita ",")
jupyter lab # Abra juypter lab
jupyter notebook
```

## Línea del PEP8
Ctrl + Shift + p $\rightarrow$ preferences
```json
"editor.rulers": [

{

"column": 80,

"color": "#d3f8ff"

},

{

"column": 120,

"color": "#ff0000"

}

],
```

### Configuración para Latex
F1 - > Open User Settings (JSON)
```json
{
    "workbench.colorTheme": "Visual Studio 2017 Dark - C++",
    "explorer.confirmDragAndDrop": false,
    "latex-workshop.latex.outDir": "%DIR%/build",
    
    // Indica a la extensión que limpie la basura automáticamente al terminar
    "latex-workshop.latex.autoClean.run": "onBuilt",
    
    // Esto asegura que el visor de PDF sepa que el archivo está en /build
    "latex-workshop.view.pdf.viewer": "tab",

    // Configuración de las herramientas de compilación
    "latex-workshop.latex.tools": [
        {
            "name": "latexmk",
            "command": "latexmk",
            "args": [
                "-shell-escape",
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdf",
                "-outdir=%OUTDIR%", // Aquí es donde usa el /build que definiste
                "%DOC%"
            ]
        }
    ]
}
```

