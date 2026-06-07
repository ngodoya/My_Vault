# Ejemplo: Archivo `pokemon_base_data.csv`

## ¿Cómo se ve?

Este es el archivo que va en la raíz del proyecto. Contiene todos los datos base de cada Pokémon.

### Archivo completo (pokemon_base_data.csv)

```csv
name,type,hp_base,hp_max,attack_base,attack_max,defense_base,defense_max,sp_attack_base,sp_attack_max,sp_defense_base,sp_defense_max,speed_base,speed_max,evolution,evolution_level
Charmander,Fire,20,120,10,65,9,64,12,90,11,75,15,100,Charmeleon,16
Charmeleon,Fire,30,155,15,95,12,85,20,115,15,95,20,130,Charizard,36
Charizard,Fire,39,180,20,134,15,108,25,159,20,115,25,160,,
Bulbasaur,Grass,20,120,10,65,10,65,12,90,13,85,15,100,Ivysaur,16
Ivysaur,Grass,30,155,13,80,13,80,16,110,16,105,18,120,Venusaur,32
Venusaur,Grass,40,190,18,102,18,102,22,142,22,130,20,140,,
Squirtle,Water,20,120,10,65,11,80,12,90,13,85,11,100,Wartortle,16
Wartortle,Water,30,155,15,90,14,100,16,110,16,100,15,130,Blastoise,36
Blastoise,Water,40,180,20,134,18,135,20,140,20,115,18,150,,
```
## Explicación Columna por Columna
| Columna           | Descripción                                              | Ejemplo    |
| ----------------- | -------------------------------------------------------- | ---------- |
| `name`            | Nombre del Pokémon                                       | Charmander |
| `type`            | Tipo (Fire, Water, Grass, etc)                           | Fire       |
| `hp_base`         | HP mínimo (nivel 1)                                      | 20         |
| `hp_max`          | HP máximo (nivel 100)                                    | 120        |
| `attack_base`     | Ataque mínimo (nivel 1)                                  | 10         |
| `attack_max`      | Ataque máximo (nivel 100)                                | 65         |
| `defense_base`    | Defensa mínima (nivel 1)                                 | 9          |
| `defense_max`     | Defensa máxima (nivel 100)                               | 64         |
| `sp_attack_base`  | Ataque Especial mínimo (nivel 1)                         | 12         |
| `sp_attack_max`   | Ataque Especial máximo (nivel 100)                       | 90         |
| `sp_defense_base` | Defensa Especial mínima (nivel 1)                        | 11         |
| `sp_defense_max`  | Defensa Especial máxima (nivel 100)                      | 75         |
| `speed_base`      | Velocidad mínima (nivel 1)                               | 15         |
| `speed_max`       | Velocidad máxima (nivel 100)                             | 100        |
| `evolution`       | Nombre del Pokémon evolucionado (vacío si no evoluciona) | Charmeleon |
| `evolution_level` | Nivel en el que evoluciona (vacío si no evoluciona)      | 16         |

## Ejemplo de Progresión: Charmander → Charmeleon

### Charmander (Nivel 1 a 15)

Fila en CSV:
``Charmander,Fire,20,120,10,65,9,64,12,90,11,75,15,100,Charmeleon,16``
Cálculo de stats en diferentes niveles:
**Nivel 1:**
```text
Attack = 10 + (1-1)/99 * (65-10) = 10 + 0 = 10
Defense = 9 + (1-1)/99 * (64-9) = 9 + 0 = 9
Speed = 15 + (1-1)/99 * (100-15) = 15 + 0 = 15
```
**Nivel 9:**
```text
Attack = 10 + (8-1)/99 * (65-10) = 10 + 7/99 * 55 = 10 + 3.89 = 13.89
Defense = 9 + (8-1)/99 * (64-9) = 9 + 7/99 * 55 = 9 + 3.89 = 12.89
Speed = 15 + (8-1)/99 * (100-15) = 15 + 7/99 * 85 = 15 + 5.98 = 20.98
```
**Nivel 15:** (antes de evolucionar:)
```text
Attack = 10 + (15-1)/99 * (65-10) = 10 + 14/99 * 55 = 10 + 7.78 = 17.78
Defense = 9 + (15-1)/99 * (64-9) = 9 + 14/99 * 55 = 9 + 7.78 = 16.78
Speed = 15 + (15-1)/99 * (100-15) = 15 + 14/99 * 85 = 15 + 11.97 = 26.97
```
### Charmeleon (Nivel 16 en adelante)

Fila en CSV:
```text
Charmeleon,Fire,30,155,15,95,12,85,20,115,15,95,20,130,Charizard,36
```
Al evolucionar, **mantiene el nivel 16** pero los stats se recalculan con los nuevos base y max:

**Nivel 16 (justo después de evolucionar):**
```code
Attack = 15 + (16-1)/99 * (95-15) = 15 + 15/99 * 80 = 15 + 12.12 = 27.12
Defense = 12 + (16-1)/99 * (85-12) = 12 + 15/99 * 73 = 12 + 11.06 = 23.06
Speed = 20 + (16-1)/99 * (130-20) = 20 + 15/99 * 110 = 20 + 16.67 = 36.67
```
Notar que: **Attack pasó de 17.78 a 27.12** (mejora significativa por evolución)
## Cómo Se Vería en Excel
| name       | type  | hp_base | hp_max | attack_base | attack_max | ... | evolution  | evolution_level |
| ---------- | ----- | ------- | ------ | ----------- | ---------- | --- | ---------- | --------------- |
| Charmander | Fire  | 20      | 120    | 10          | 65         | ... | Charmeleon | 16              |
| Charmeleon | Fire  | 30      | 155    | 15          | 95         | ... | Charizard  | 36              |
| Bulbasaur  | Grass | 20      | 120    | 10          | 65         | ... | Ivysaur    | 16              |
```python
import csv

# Leer el CSV
pokemon_data = {}

with open("pokemon_base_data.csv", mode="r", encoding="utf-8") as file:
    reader = csv.DictReader(file)
    
    for row in reader:
        pokemon_data[row["name"]] = row
        print(row)
        # Output:
        # {'name': 'Charmander', 'type': 'Fire', 'hp_base': '20', 'hp_max': '120', ...}
        # {'name': 'Charmeleon', 'type': 'Fire', 'hp_base': '30', 'hp_max': '155', ...}


charmander_data = pokemon_data["Charmander"]
print(charmander_data["attack_base"]) 
print(charmander_data["evolution"]) 
```

## Ventajas de Este Enfoque
**Sin CSV (Hardcodeado en Python):**
```python
class Charmander(Pokemon):
    def __init__(self):
        super().__init__(
            name="Charmander",
            hp_base=20,
            hp_max=120,
            attack_base=10,
            attack_max=65,
            # ... 12 líneas más de stats
        )

class Charmeleon(Pokemon):
    def __init__(self):
        super().__init__(
            name="Charmeleon",
            hp_base=30,
            hp_max=155,
            # ... 12 líneas más de stats
        )

# Si tienes 20 Pokémon = 20 clases + 240 líneas de código
```
**Con CSV (Centralizado):**
```python
# Solo 2 líneas de código, datos en 1 archivo CSV
charmander = Pokemon("Charmander", ["Fire"], Stats(), level=1)
charmeleon = Pokemon("Charmeleon", ["Fire"], Stats(), level=16)

# Si tienes 100 Pokémon = 100 líneas en CSV, cero código extra
```
## Cómo Agregar Nuevos Pokémon

Solo agrega una fila al CSV:
```csv
Pikachu,Electric,20,95,10,75,11,75,12,110,10,90,15,120,Raichu,16 
```
