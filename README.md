# Sala de Estudio

## Descripción del sistema
Aplicación web que permite visualizar la disponibilidad de salas de estudio en la universidad, reservar espacios, cancelar reservas y consultar información relevante como ubicación, capacidad y equipamiento. El sistema reemplaza el proceso actual basado en correos electrónicos, facilitando la gestión de salas de forma centralizada y eficiente.

## Historias de Usuario
Todas las historias están registradas como GitHub Issues.

| ID    | Nombre                                      | Issue |
|-------|----------------------------------------------|-------|
| US-01 | Visualizar disponibilidad de salas           | #3    |
| US-02 | Reservar sala de estudio                     | #5    |
| US-03 | Ver ubicación de salas                       | #3    |
| US-04 | Ver capacidad de salas                       | #4    |
| US-05 | Reservar sala rápidamente                    | #5    |
| US-06 | Cancelar reserva                             | #6    |
| US-07 | Prioridad por facultad                       | #7    |
| US-08 | Ver equipamiento de salas                    | #8    |

## Requisitos Extrafuncionales
Ver: [ReqExtrafuncionales.md](./ReqExtrafuncionales.md)

## Entidades del Dominio

Usuario:
- id
- nombre
- facultad

Sala:
- id
- ubicación
- capacidad
- equipamiento

Reserva:
- id
- fecha
- usuario
- sala
- estado

## Mockups

| Mockup | Historia de usuario relacionada |
|--------|--------------------------------|
| Pantalla listado de salas | US-01 |
| Pantalla reserva | US-02 |
| Pantalla mis reservas | US-06 |

## Diseño Arquitectónico
Ver: [Arquitectura.md](./Arquitectura.md)

## Responsabilidades del equipo

| Integrante | Rol | Ítems de la rúbrica a cargo |
|------------|-----|----------------------------|
| José Ignacio Leiva | Analista de requisitos | Completitud, correctitud y calidad de historias de usuario |
| Vicente Araya | Arquitecto de software | Estilo arquitectónico, módulos y consistencia del diseño |
| Matías Henríquez | Encargado de requisitos extrafuncionales | Catálogo, priorización y relación con arquitectura |
| Martín Leon | Encargado de dominio e interfaz | Entidades del dominio, mockups y consistencia con HU |
