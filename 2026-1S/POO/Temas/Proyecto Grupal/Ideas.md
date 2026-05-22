# Ejemplo de estructura del proyecto

```text
pet_manager/
│
├── core/
│   ├── sistema.py
│
├── models/
│   ├── mascota.py
│   ├── dueno.py
│   ├── veterinario.py
│   ├── cita.py
│   ├── historial.py
│
├── services/
│   ├── gestor_mascotas.py
│   ├── gestor_citas.py
│   ├── gestor_reportes.py
│
├── persistence/
│   ├── json_manager.py
│
├── utils/
│   ├── validaciones.py
│
├── main.py
├── requirements.txt
└── README.md
```

---

# UML

```mermaid
classDiagram
    direction TB

    namespace core {
        class SistemaVeterinaria {
            -gestor_mascotas: GestorMascotas
            -gestor_duenos: GestorDuenos
            -gestor_veterinarios: GestorVeterinarios
            -gestor_citas: GestorCitas
            -json_manager: JSONManager
            +iniciar_sistema()
            +cerrar_sistema()
        }
    }

    namespace models {
        class Persona {
            <<Abstract>>
            #id: string
            #nombre: string
        }
        class Dueno {
            +telefono: string
            +email: string
            +mascotas_ids: list
        }
        class Veterinario {
            +especialidad: string
        }
        class Mascota {
            +id: string
            +nombre: string
            +especie: string
            +dueno_id: string
            +historial_id: string
        }
        class Cita {
            +id: string
            +fecha_hora: datetime
            +mascota_id: string
            +veterinario_id: string
        }
        class HistorialMedico {
            +id: string
            +entradas: list
        }
    }

    namespace services {
        class Gestor {
            <<Abstract>>
            #elementos: dict
            +obtener_por_id(id)
            +obtener_todos()
        }
        class GestorMascotas
        class GestorDuenos
        class GestorVeterinarios
        class GestorCitas
    }

    namespace persistence {
        class JSONManager {
            +guardar_datos(archivo, datos)
            +cargar_datos(archivo)
        }
    }

    models.Persona <|-- models.Dueno
    models.Persona <|-- models.Veterinario
    services.Gestor <|-- services.GestorMascotas
    services.Gestor <|-- services.GestorDuenos
    services.Gestor <|-- services.GestorVeterinarios
    services.Gestor <|-- services.GestorCitas

    core.SistemaVeterinaria o-- services.GestorMascotas
    core.SistemaVeterinaria o-- services.GestorDuenos
    core.SistemaVeterinaria o-- services.GestorVeterinarios
    core.SistemaVeterinaria o-- services.GestorCitas
    
    core.SistemaVeterinaria ..> persistence.JSONManager : usa
    services.GestorDuenos ..> models.Dueno : gestiona
    services.GestorMascotas ..> models.Mascota : gestiona
    services.GestorCitas ..> models.Cita : gestiona
    models.Dueno "1" -- "*" models.Mascota : tiene (por ID)
    models.Cita "1" -- "1" models.Mascota : para
    models.Cita "1" -- "1" models.Veterinario : con
    models.Mascota "1" -- "1" models.HistorialMedico : tiene
```

