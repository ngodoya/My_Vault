# Airport Check-In System: Estrategia y Arquitectura

## Misión del Proyecto

Construir una simulación robusta, orientada a objetos e impulsada por eventos para el flujo de check-in de un aeropuerto. El sistema garantiza encapsulamiento, manejo seguro de errores mediante excepciones personalizadas y un procesamiento eficiente utilizando colas de prioridad y generadores.

---

## 5 Conceptos Clave

1. **Abstracción y Contratos (`Luggage` como ABC):**
   Definir `Luggage` como una clase abstracta (`abc.ABC`) asegura que no existan instancias de equipaje sin un tipo definido y obliga a todas las subclases a implementar su propia lógica de validación de peso (`validate_weight()`).

2. **Encapsulamiento y Ocultamiento de Información (`Passenger` y `Flight`):**
   Los datos sensibles (como el número de documento) y los estados internos complejos (como el registro de pases de abordar) no se exponen directamente. Se gestionan mediante métodos de acceso (`get_masked_id()`) e interfaces de iteración (`__iter__()`).

3. **Manejo Controlado de Excepciones Propias (`exceptions.py`):**
   El sistema no interrumpe abruptamente su ejecución ante fallos de negocio. Modela situaciones del dominio real mediante excepciones dedicadas (`FlightFullError`, `OverweightLuggageError`, `EmptyQueueError`), separando la lógica de validación de la lógica de presentación.

4. **Colas de Prioridad Bidireccionales (`CheckInQueue`):**
   Implementa reglas de atención reales combinando dos estructuras FIFO (`collections.deque`). Garantiza que los pasajeros VIP siempre sean procesados antes que los pasajeros de la fila regular.

5. **Flujos Perezosos y Evaluación Bajo Demanda (`Generators` en `CheckInCounter`):**
   El proceso de check-in no acumula resultados en memoria. Utiliza la instrucción `yield` en el método `process_queue()` para procesar y entregar el resultado de cada pasajero individualmente a medida que es atendido.

---

## Preguntas Clave para el Equipo (Sanity Checks)

### Lógica de Negocio y Errores
- **¿Un pasajero rechazado consume un asiento del vuelo?**
  No. Si un pasajero falla la validación de equipaje (`OverweightLuggageError`), el proceso debe interrumpirse antes de ejecutar `assign_seat()`.
- **¿Cómo debe comportarse el iterador de `Flight`?**
  El método `__iter__(self)` debe permitir recorrer los pases de abordar emitidos sin exponer directamente la lista interna `_boarding_passes`. Se puede retornar `iter(self._boarding_passes)`.

### Gestión de Colas
- **¿Cómo evita `process_queue()` lanzar `EmptyQueueError` durante la ejecución normal?**
  `process_queue()` debe consultar si existen elementos en la cola VIP o en la regular antes de invocar `next_passenger()`. La excepción `EmptyQueueError` se reserva exclusivamente para llamadas directas e indebidas a `next_passenger()` cuando la estructura está vacía.

### Diagrama UML y Sintaxis Python
- **¿Cómo se representan los modificadores de acceso en UML frente a Python?**
  - Privado: `-` en UML, mapeado a `__atributo` en Python (ej. `__document_id`).
  - Protegido: `#` en UML, mapeado a `_atributo` en Python (ej. `_assigned_seats`).
  - Público: `+` en UML, mapeado a `atributo` o `metodo()` público en Python.

---

## Distribución Preliminar de Tareas por Tópicos

### Módulo 1: Core Domain y Encapsulamiento
- **Archivos:** `models.py`
- **Componentes:** `Passenger`, `Flight`
- **Entregables:**
  - Clase `Passenger` con atributo privado `__document_id` y método `get_masked_id()` utilizando slicing de cadenas.
  - Clase `Flight` con control de capacidad, asignación de asientos y soporte para el protocolo de iteración `__iter__()`.

### Módulo 2: Jerarquía de Clases y Polimorfismo
- **Archivos:** `models.py`
- **Componentes:** `Luggage`, `CarryOn`, `CheckedLuggage`
- **Entregables:**
  - Clase abstracta `Luggage` heredando de `abc.ABC` con `@abstractmethod validate_weight()`.
  - Subclase `CarryOn` (límite 10 kg).
  - Subclase `CheckedLuggage` (límite 23 kg).
  - Lógica para lanzar `OverweightLuggageError` en caso de exceso de peso.

### Módulo 3: Excepciones y Estructuras de Datos
- **Archivos:** `exceptions.py`, `queueing.py`
- **Componentes:** Excepciones personalizadas, `CheckInQueue`
- **Entregables:**
  - Definición de `FlightFullError`, `OverweightLuggageError` y `EmptyQueueError` heredando de `Exception`.
  - Clase `CheckInQueue` que administre `_vip_queue` y `_regular_queue` utilizando `collections.deque`.
  - Método `next_passenger()` con prioridad VIP y lanzamiento de `EmptyQueueError`.

### Módulo 4: Lógica de Servicio y Generadores
- **Archivos:** `models.py`, `counter.py`
- **Componentes:** `BoardingPass`, `CheckInCounter`
- **Entregables:**
  - Clase `BoardingPass` con método `print_pass()` para representación formateada.
  - Método `CheckInCounter.check_in()` para coordinar validación de equipaje y asignación de asiento.
  - Método generador `CheckInCounter.process_queue()` utilizando `yield` para procesar la fila elemento a elemento.

### Módulo 5: Integración, UML y Demostración
- **Archivos:** `main.py`, `README.md`, Diagrama UML
- **Componentes:** Script principal y documentación
- **Entregables:**
  - Diagrama de clases UML completo con tipos, multiplicidades y modificadores de acceso.
  - Script `main.py` protegido con `if __name__ == "__main__":` ejecutando todos los escenarios requeridos.
  - Verificación del paquete Python e historial de commits integrado.