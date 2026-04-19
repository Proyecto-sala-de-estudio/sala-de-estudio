# Sala de Estudio

## Descripción del sistema
Sala de Estudio es una aplicación web orientada a estudiantes universitarios para visualizar salas de estudio disponibles, reservar espacios, cancelar reservas y consultar información relevante como ubicación, capacidad y equipamiento. Además, considera funcionalidades de administración para gestionar salas, visualizar estadísticas de uso y configurar reglas del sistema.

## Historias de Usuario
Todas las historias están registradas como GitHub Issues.

| ID    | Nombre                           | Issue |
|-------|----------------------------------|-------|
| US-01 | Ver ubicación de salas           | #1    |
| US-02 | Ver capacidad de salas           | #2    |
| US-03 | Reservar sala rápidamente        | #3    |
| US-04 | Cancelar reserva                 | #4    |
| US-05 | Prioridad por facultad           | #5    |
| US-06 | Ver equipamiento de salas        | #6    |
| US-07 | Ver equipamiento de salas        | #7    |
| US-08 | Gestionar salas                  | #8    |
| US-09 | Ver uso de salas                 | #9    |
| US-10 | Configurar reglas del sistema    | #10   |

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

| Mockup | Historia de usuario relacionada |(Preguntar profe)
|--------|----------------------------------|
| Lista de salas disponibles(pegar link  figma ) | US-01 |




## Diseño Arquitectónico
Ver: [Arquitectura.md](./Arquitectura.md)

## Responsabilidades del equipo

| Integrante | Rol | Ítems de la rúbrica a cargo |
|------------|-----|-----------------------------|
| José Ignacio Leiva | Analista de requisitos | Completitud, correctitud y calidad de historias de usuario (issues) |
| Vicente Araya | Arquitecto de software | Estilo arquitectónico, descomposición modular, consistencia del diagrama y decisiones de diseño |
| Matías Henríquez | Encargado de requisitos extrafuncionales | Catálogo de REF, clasificación, priorización y relación con la arquitectura |
| Martín Leon | Encargado de dominio e interfaz | Entidades del dominio, mockups y coherencia con historias de usuario |


