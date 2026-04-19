## 1. Estilo Arquitectónico

Estilo adoptado: Cliente-Servidor (Arquitectura en capas)

Justificación basada en REF priorizados:

| REF ID | Descripción                              | Prioridad | Cómo lo aborda el estilo |
|--------|------------------------------------------|-----------|--------------------------|
| REF-01 | Tiempo de respuesta < 2 segundos         | Alta      | API REST permite respuestas rápidas y eficientes |
| REF-02 | Disponibilidad >= 99%                    | Alta      | Separación frontend/backend mejora disponibilidad |
| REF-03 | Autenticación obligatoria                | Alta      | Backend centraliza control de acceso |
| REF-04 | Interfaz simple e intuitiva              | Alta      | Frontend desacoplado permite mejor UX |
| REF-10 | Consistencia de datos de reservas        | Alta      | Backend controla lógica de negocio y validaciones |

Explicación textual:  
Se adopta una arquitectura cliente-servidor en capas, donde el frontend se encarga de la interacción con el usuario, el backend gestiona la lógica de negocio y la base de datos almacena la información.  
Este estilo permite abordar los requisitos extrafuncionales de alto nivel, asegurando un sistema eficiente, seguro, disponible y mantenible.  
Además, facilita la escalabilidad y la separación de responsabilidades, permitiendo futuras mejoras sin afectar todo el sistema.

---

## 2. Diagrama de Arquitectura

![Diagrama de Arquitectura](./diagrama_arquitectura.png)

---

## 3. Descomposición Modular

Fundamentación:  
La descomposición se realiza por capas funcionales, separando responsabilidades en frontend, backend y base de datos, con el objetivo de mantener bajo acoplamiento y alta cohesión.

### Módulo 1: Frontend
- Responsabilidad: Interfaz de usuario y visualización de información
- Ofrece a otros módulos: Solicitudes HTTP al backend
- Depende de: Backend API

### Módulo 2: Backend API
- Responsabilidad: Lógica de negocio, gestión de reservas y usuarios
- Ofrece a otros módulos: Endpoints API REST
- Depende de: Base de datos

### Módulo 3: Base de Datos
- Responsabilidad: Almacenamiento de información de usuarios, salas y reservas
- Ofrece a otros módulos: Persistencia de datos
- Depende de: Ninguno

---

## 4. Decisiones de Diseño

### Decisión 1
- Decisión: Uso de API REST para comunicación entre frontend y backend
- Motivación: Permitir una comunicación eficiente y escalable (REF-01, REF-09)
- Alternativas consideradas: Comunicación directa con base de datos (descartada por falta de seguridad y control)
- Impacto: Mejora escalabilidad y separación de responsabilidades

### Decisión 2
- Decisión: Separación en capas (frontend, backend, base de datos)
- Motivación: Cumplir con mantenibilidad y bajo acoplamiento (REF-07)
- Alternativas consideradas: Aplicación monolítica
- Impacto: Facilita mantenimiento y evolución del sistema

### Decisión 3
- Decisión: Validación de reservas en backend
- Motivación: Garantizar consistencia de datos (REF-10)
- Alternativas consideradas: Validación en frontend
- Impacto: Evita inconsistencias y errores en reservas
