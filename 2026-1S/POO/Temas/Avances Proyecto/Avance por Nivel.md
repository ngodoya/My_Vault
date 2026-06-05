# Análisis del Sistema de Subida de Nivel y Estadísticas

## Situación Actual

El código implementa un sistema de subida de nivel con incremento **aleatorio** de estadísticas:

```python
self.stats.attack += random.randint(1, 3)
self.stats.defense += round(random.uniform(0.2, 1.0), 2)
self.stats.special_attack += random.randint(1, 3)
self.stats.special_defense += round(random.uniform(0.2, 1.0), 2)
self.stats.speed += round(random.uniform(0.2, 1.0), 2)
self.stats.hp += random.randint(4, 8)
```
**Problema:** Las estadísticas suben de forma aleatoria dentro de rangos fijos, sin considerar:

- Las estadísticas **base** de cada especie Pokémon
- Un **techo máximo** (estadística máxima esperada a nivel 100)
- Una **progresión predecible y escalable**
**Fórmula Lineal:**
$Stat_{Actual} = Stat_{Base} + (Nivel - 1) / 99 * (Stat_{Max} - Stat_{Base})$

|Nivel|Fórmula|Ataque|
|---|---|---|
|1|15 + (0/99) * 85|15|
|5|15 + (4/99) * 85|~18.44|
|50|15 + (49/99) * 85|~57.5|
|100|15 + (99/99) * 85|100|

1. **¿Es correcta la fórmula lineal que propusimos?**  
   `Stat_Actual = Stat_Base + (Nivel - 1) / 99 * (Stat_Max - Stat_Base)`  
   ¿O deberíamos usar otro modelo matemático (cuadrático, logarítmico)?

2. **¿Hasta qué punto debemos simplificar el sistema de estadísticas?**  
   - ¿Solo Base Stats + Nivel?
   - ¿O también implementar Puntos de Esfuerzo (EVs)?

3. **¿Cómo debemos estructurar los datos base de cada Pokémon?**  
   - ¿Hardcodeados en cada clase (Charmeleon, Charmander)?
   - ¿De un archivo externo (JSON, CSV)?

4. **¿Las estadísticas se recalculan completamente cada level-up o solo se incrementan diferencialmente?**

5. **¿Deberíamos actualizar la clase `Stats` para que sea dinámica según el nivel, o mantenerla como se encuentra?**