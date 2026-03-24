# UML: Primeros Avances
### Marzo
---
[[2026-03-14]]
[[2026-03-15]]


---
# Actividad 01
[[Actividad 01]]
---
# Inquietudes Resueltas Por El Docente

## Actividad 01
En esta sección se incluyen las dudas generadas por los estudiantes del curso hacia el docente y sus respectivas respuestas. El objetivo es centralizar esta información para que no se pierda en el historial de chats de WhatsApp o canales de Slack.

* **Pregunta:** Sobre los tests, vi que se usaba `pytest` en el anterior repo de Pokémon, ¿ese se utilizará aquí también?
    * **Respuesta:** Sí, la idea es usar `pytest`. Igual son cosas muy sencillas: por ejemplo, si creo un Pokémon con 20 puntos de vida, confirmar que efectivamente haya quedado con 20 puntos de vida.

* **Pregunta:** ¿Los métodos deben tener validaciones internas? Por ejemplo, ¿evitar de una vez que un Pokémon llegue a un HP negativo?
    * **Respuesta:** No. De momento es más el esqueleto de las clases con una lógica muy básica; ya luego le agregaremos las validaciones extras.

* **Pregunta:** ¿Considera hacer un repositorio aparte y, cuando ya tengamos una primera solución, enviamos un fork al repositorio principal?
    * **Respuesta:** La idea es que cada grupo saque su **fork** y trabaje ahí. Cuando tengan la solución, realizan un **Pull Request (PR)** a la rama `dev` del repositorio de la clase.

* **Pregunta:** ¿A futuro tenemos que pensar en atributos privados tipo getters para los objetos?
    * **Respuesta:** Vamos paso a paso. La idea es ir poniendo actividades conforme se avanza en el tema. Ahora que vimos clases, definimos clases; cuando veamos encapsulamiento, pondremos setters y getters.

* **Pregunta:** ¿El Pokémon de prueba debe ejecutarse automáticamente al correr `main.py` o solo debe ser un objeto instanciado?
    * **Respuesta:** Puede ser en `main.py`, aunque lo ideal es que vaya en los **tests**.