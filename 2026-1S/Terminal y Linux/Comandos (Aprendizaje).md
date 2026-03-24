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