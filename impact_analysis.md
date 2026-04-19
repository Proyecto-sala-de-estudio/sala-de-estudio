# impact_analysis.md – Template

## 1. Cambio solicitado
Se solicita agregar la funcionalidad de **notificaciones automáticas al usuario**, para informar sobre confirmaciones de reserva, cancelaciones y recordatorios antes del horario reservado.

---

## 2. Nuevas historias de usuario

### US-09: Recibir notificaciones de reserva
Como estudiante,  
quiero recibir notificaciones sobre el estado de mis reservas,  
para estar informado y no olvidar mis horarios.

Criterios de aceptación:
- CA1: Dado que realizo una reserva, cuando esta se confirma, entonces recibo una notificación.
- CA2: Dado que tengo una reserva próxima, cuando se acerca el horario, entonces recibo un recordatorio.

---

## 3. Impacto en requisitos extrafuncionales

Indicar si el cambio altera la prioridad de algún REF o introduce nuevos.

| REF ID | Descripción                          | Prioridad anterior | Prioridad nueva | Cambio / Motivo                  |
|--------|--------------------------------------|--------------------|-----------------|----------------------------------|
| REF-03 | Autenticación obligatoria             | Alta               | Alta            | Sin cambio                       |
| REF-01 | Tiempo de respuesta < 2s              | Alta               | Alta            | Se mantiene crítica              |
| REF-09 | Soportar múltiples usuarios           | Media              | Alta            | Aumenta carga por notificaciones |
| REF-11 | Sistema de notificaciones             | —                  | Alta            | Nuevo requisito                  |

---

## 4. Impacto en entidades del dominio

Se agrega un nuevo atributo o entidad:

**Notificación**
- id
- tipo
- mensaje
- usuario
- fecha

También se puede asociar a la entidad Reserva.

---

## 5. Impacto en mockups

Se deben agregar cambios en la interfaz:

- Notificaciones visibles en la interfaz (icono o panel)
- Mensajes emergentes de confirmación de reserva
- Avisos de recordatorio de reserva

---

## 6. Impacto en arquitectura

### 6.1 ¿Cambia el estilo arquitectónico?
No cambia — el estilo cliente-servidor sigue siendo válido.  
Sin embargo, se debe extender el backend para soportar el envío de notificaciones.

### 6.2 Relación REF (repriorizado) con decisiones de arquitectura

| REF ID | Prioridad nueva | Decisión de arquitectura que lo aborda         |
|--------|-----------------|------------------------------------------------|
| REF-09 | Alta            | Backend preparado para manejar concurrencia    |
| REF-11 | Alta            | Incorporación de módulo de notificaciones      |

---

## 7. Impacto en módulos

| Módulo             | Tipo de impacto | Responsabilidad actualizada              | Ofrece a otros |
|--------------------|----------------|------------------------------------------|----------------|
| Backend API        | modificado     | Gestionar notificaciones                 | API de notificaciones |
| Frontend           | modificado     | Mostrar notificaciones                   | UI actualizada |
| Módulo Notificaciones | nuevo       | Generar y enviar notificaciones          | Servicios de notificación |

Fundamentación de cambios modulares:  
Se agrega un nuevo módulo para manejar notificaciones, permitiendo mantener bajo acoplamiento y facilitar la escalabilidad del sistema.

---

## 8. Nuevas decisiones de diseño

### Decisión 1
- Decisión: Implementar módulo de notificaciones en el backend  
- Motivación: Incorporar nueva funcionalidad solicitada (REF-11)  
- Alternativas consideradas: Notificaciones solo en frontend (descartada por limitación funcional)  
- Impacto: Afecta backend y frontend  

---

## 9. Trazabilidad actualizada

| Historia | REF relacionado | Módulo     | Mockup  |
|----------|-----------------|------------|---------|
| US-09    | REF-11          | Backend    | Notificaciones UI |

---

## 10. Justificación global y trade-offs

La incorporación de notificaciones mejora la experiencia del usuario y reduce la probabilidad de olvidar reservas.  
Sin embargo, implica mayor carga en el sistema y mayor complejidad en el backend.  

Trade-offs:
- Se gana usabilidad y funcionalidad  
- Se sacrifica simplicidad y se aumenta la complejidad del sistema  

La solución es coherente con la arquitectura existente y permite escalar el sistema en el futuro.
