# impact_analysis.md – Template

## 1. Cambio solicitado
Se solicita agregar la funcionalidad de notificaciones automáticas para reservas y administración, de modo que los estudiantes reciban avisos sobre confirmaciones, cancelaciones y modificaciones de reserva, y los administradores reciban alertas sobre alta demanda o conflictos de uso.

## 2. Nuevas historias de usuario

### US-12: Recibir notificaciones de reserva
Como estudiante,  
quiero recibir notificaciones sobre mis reservas,  
para mantenerme informado sobre cambios en mis horarios de estudio.

Criterios de aceptación:
- CA1: Dado que realizo una reserva, cuando esta se confirma, entonces recibo una notificación.
- CA2: Dado que una reserva es cancelada o modificada, cuando el sistema procesa el cambio, entonces recibo una notificación actualizada.

### US-13: Recibir alertas de uso del sistema
Como administrador,  
quiero recibir alertas sobre conflictos o alta demanda de salas,  
para tomar decisiones de gestión oportunas.

Criterios de aceptación:
- CA1: Dado que una sala presenta alta demanda, cuando el sistema detecta el evento, entonces se genera una alerta para administración.
- CA2: Dado que se produce un conflicto de uso o disponibilidad, cuando el sistema lo detecta, entonces se notifica al administrador.

## 3. Impacto en requisitos extrafuncionales

Indicar si el cambio altera la prioridad de algún REF o introduce nuevos.  
Trazar cambios de prioridad que motiven cambios en decisiones de arquitectura.

| REF ID | Descripción                                                                | Prioridad anterior | Prioridad nueva | Cambio / Motivo |
|--------|----------------------------------------------------------------------------|--------------------|-----------------|-----------------|
| REF-01 | El sistema debe responder en menos de 2 segundos en operaciones comunes    | Alta               | Alta            | Sin cambio |
| REF-02 | El sistema debe estar disponible al menos un 99% en horario operativo      | Alta               | Alta            | Sin cambio |
| REF-09 | El sistema debe soportar múltiples usuarios concurrentes                   | Media              | Alta            | Las notificaciones aumentan carga concurrente |
| REF-10 | Los datos de reservas deben mantenerse consistentes en todo momento        | Alta               | Alta            | Se vuelve más crítico al informar cambios automáticos |
| REF-11 | El sistema debe emitir notificaciones oportunas y consistentes             | —                  | Alta            | Nuevo requisito derivado del cambio |

## 4. Impacto en entidades del dominio

Se agrega una nueva entidad:

### Notificacion
- id
- tipo
- mensaje
- fecha
- leida
- usuario_id

Relaciones afectadas:
- Un Usuario puede recibir múltiples Notificaciones
- Una Reserva puede generar una o más Notificaciones
- La Administración puede recibir notificaciones asociadas a eventos del sistema

## 5. Impacto en mockups

Mockups afectados y descripción de cambios necesarios:
- **Pantalla de reserva**: mostrar confirmación de reserva y cambios recientes
- **Mis reservas**: mostrar notificaciones relacionadas con cancelaciones o modificaciones
- **Panel de administración**: mostrar alertas de demanda o conflictos del sistema
- **Nuevo componente**: campana o bandeja de notificaciones

## 6. Impacto en arquitectura

### 6.1 ¿Cambia el estilo arquitectónico?
No — Justificación:  
La arquitectura cliente-servidor en capas sigue siendo válida. El cambio agrega una nueva responsabilidad funcional, pero no obliga a modificar el estilo arquitectónico. La solución puede integrarse mediante una extensión del backend y un módulo adicional de notificaciones.

### 6.2 Relación REF (repriorizado) con decisiones de arquitectura

| REF ID | Prioridad nueva | Decisión de arquitectura que lo aborda |
|--------|-----------------|----------------------------------------|
| REF-09 | Alta            | Extender backend para gestionar eventos concurrentes y envío de avisos |
| REF-10 | Alta            | Centralizar notificaciones en backend para asegurar coherencia con cambios reales |
| REF-11 | Alta            | Incorporar módulo específico de notificaciones |

## 7. Impacto en módulos

| Módulo | Tipo de impacto | Responsabilidad actualizada | Ofrece a otros (actualizado) |
|--------|------------------|-----------------------------|------------------------------|
| Interfaz de Usuario | modificado | Mostrar notificaciones a estudiantes y administradores | Visualización de avisos y alertas |
| Gestión de Reservas | modificado | Generar eventos al crear, cancelar o modificar reservas | Información para módulo de notificaciones |
| Administración | modificado | Mostrar alertas de uso y conflictos | Panel de alertas administrativas |
| Backend API | modificado | Exponer endpoints para consulta de notificaciones | Servicios REST de notificaciones |
| Módulo de Notificaciones | nuevo | Generar, almacenar y distribuir notificaciones | Envío y consulta de avisos |
| Base de Datos | modificado | Persistir notificaciones emitidas por el sistema | Almacenamiento de mensajes y estado |

Fundamentación de cambios modulares:  
Se agrega un módulo específico de notificaciones para separar esta responsabilidad del resto del sistema. Esto permite mantener alta cohesión, bajo acoplamiento y una mejor trazabilidad entre eventos del sistema y avisos emitidos a usuarios o administradores.

## 8. Nuevas decisiones de diseño

### Decisión 1
- Decisión: Incorporar un módulo de notificaciones independiente
- Motivación: Separar la lógica de avisos del resto de la lógica de reservas y administración (REF-07, REF-11)
- Alternativas consideradas: Gestionar notificaciones dentro de Gestión de Reservas
- Impacto: Afecta Backend API, Base de Datos, Interfaz de Usuario y Administración

### Decisión 2
- Decisión: Generar notificaciones desde el backend a partir de eventos reales del sistema
- Motivación: Asegurar consistencia entre el estado del sistema y los avisos enviados (REF-10)
- Alternativas consideradas: Generar avisos solo desde frontend
- Impacto: Reduce inconsistencias y mejora confiabilidad de la información entregada

## 9. Trazabilidad actualizada

| Historia | REF relacionado | Módulo | Mockup |
|----------|-----------------|--------|--------|
| US-12 | REF-10, REF-11 | Módulo de Notificaciones | Bandeja de notificaciones |
| US-13 | REF-09, REF-11 | Administración / Módulo de Notificaciones | Panel de alertas |

## 10. Justificación global y trade-offs

La incorporación de notificaciones mejora la experiencia de estudiantes y administradores, ya que permite reaccionar oportunamente frente a cambios, conflictos o eventos importantes del sistema. La solución es coherente con el diseño actual porque mantiene el estilo arquitectónico base y extiende el sistema mediante un módulo bien delimitado.

Trade-offs considerados:
- Se gana visibilidad, trazabilidad y mejor comunicación con usuarios
- Se sacrifica simplicidad, ya que aumenta la complejidad del backend y la cantidad de eventos a gestionar
- Se requiere mayor control de consistencia para evitar notificaciones erróneas o desactualizadas
