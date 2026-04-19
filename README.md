# Sala de Estudio

## Descripción del sistema
Sala de Estudio es una aplicación web orientada a estudiantes universitarios para visualizar salas de estudio disponibles, reservar espacios, cancelar reservas y consultar información relevante como ubicación, capacidad y equipamiento. Además, considera funcionalidades de administración para gestionar salas, visualizar estadísticas de uso y configurar reglas del sistema.

## Historias de Usuario
Todas las historias están registradas como GitHub Issues.

| ID    | Nombre                           | Issue |
|-------|----------------------------------|-------|
| US-01 | Ver ubicación de salas           | #3    |
| US-02 | Ver capacidad de salas           | #4    |
| US-03 | Reservar sala rápidamente        | #5    |
| US-04 | Cancelar reserva                 | #6    |
| US-05 | Prioridad por facultad           | #7    |
| US-06 | Ver equipamiento de salas        | #8    |
| US-07 | Ver mis reservas                 | #14   |
| US-08 | Modificar reserva                | #15   |
| US-09 | Gestionar salas                  | #11   |
| US-10 | Ver uso de salas                 | #12   |
| US-11 | Configurar reglas del sistema    | #13   |

## Requisitos Extrafuncionales
Ver: [ReqExtrafuncionales.md](./ReqExtrafuncionales.md)

## Entidades del Dominio

### Usuario
- id
- nombre
- correo
- facultad
- rol

### Sala
- id
- nombre
- ubicación
- capacidad
- equipamiento
- facultad
- estado

### Reserva
- id
- fecha
- hora_inicio
- hora_fin
- estado
- usuario_id
- sala_id

### ReglaSistema
- id
- nombre
- valor
- descripción

## Mockups

| Mockup | Historia de usuario relacionada |
|--------|----------------------------------|
| Lista de salas disponibles | US-01 |
| Detalle de sala | US-02 |
| Pantalla de reserva | US-03 |
| Mis reservas | US-04 |
| Salas priorizadas por facultad | US-05 |
| Detalle de equipamiento | US-06 |
| Vista de reservas activas | US-07 |
| Edición de reserva | US-08 |
| Panel de administración de salas | US-09 |
| Panel de estadísticas | US-10 |
| Configuración de reglas | US-11 |

## Diseño Arquitectónico
Ver: [Arquitectura.md](./Arquitectura.md)

## Responsabilidades del equipo

| Integrante | Rol | Ítems de la rúbrica a cargo |
|------------|-----|-----------------------------|
| José Ignacio Leiva | Analista de requisitos | Completitud, correctitud y calidad de historias de usuario (issues) |
| Vicente Araya | Arquitecto de software | Estilo arquitectónico, descomposición modular, consistencia del diagrama y decisiones de diseño |
| Matías Henríquez | Encargado de requisitos extrafuncionales | Catálogo de REF, clasificación, priorización y relación con la arquitectura |
| Martín Leon | Encargado de dominio e interfaz | Entidades del dominio, mockups y coherencia con historias de usuario |

## Trazabilidad

| Historia | REF relacionado | Módulo | Mockup |
|----------|-----------------|--------|--------|
| US-01 | REF-04 | Gestión de Salas | Lista de salas disponibles |
| US-02 | REF-04 | Gestión de Salas | Detalle de sala |
| US-03 | REF-01, REF-03, REF-10 | Gestión de Reservas | Pantalla de reserva |
| US-04 | REF-03, REF-10 | Gestión de Reservas | Mis reservas |
| US-05 | REF-03, REF-04 | Gestión de Salas / Gestión de Usuarios | Salas priorizadas por facultad |
| US-06 | REF-04 | Gestión de Salas | Detalle de equipamiento |
| US-07 | REF-04 | Gestión de Reservas | Vista de reservas activas |
| US-08 | REF-10 | Gestión de Reservas | Edición de reserva |
| US-09 | REF-07 | Administración | Panel de administración de salas |
| US-10 | REF-01 | Administración | Panel de estadísticas |
| US-11 | REF-07, REF-10 | Administración | Configuración de reglas |
