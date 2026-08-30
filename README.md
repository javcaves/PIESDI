# Proyecto PIESDI: Sistema Integral de Gestión, Trazabilidad y Análisis de Adecuaciones Curriculares

Propuesta de modernización tecnológica para la gestión de apoyos inclusivos universitarios, enfocada en la automatización de notificaciones docentes y análisis histórico de datos.

## El Problema
Actualmente, el proceso de gestión de adecuaciones curriculares presenta tres desafíos críticos:
1. **Desintegración de Datos:** El historial de apoyos y los resultados de encuestas de satisfacción viven en planillas aisladas.
2. **Pérdida de Conocimiento:** Dificultad para consultar rápidamente qué adecuaciones han tenido mayor porcentaje de éxito estadístico según el perfil del estudiante.

## La Solución
Un sistema centralizado que acompaña todo el ciclo de vida de una adecuación curricular, dividido en los siguientes módulos:

### Módulo 1: Repositorio Centralizado y Gestión de Casos
Base de datos relacional para el registro estructurado de estudiantes, diagnósticos y tipos de adecuación aprobadas, eliminando la duplicidad de información.

### Módulo 2: Dashboards y Cruce de Satisfacción
Integración de datos históricos y encuestas de estudiantes pasados para calcular estadísticas cruzadas (Eficacia vs. Percepción) mediante paneles visuales institucionales.


## Arquitectura Técnica Propuesta

* **Base de Datos:** PostgreSQL (Modelo relacional estructurado para escalabilidad).
* **Backend / API:** Lógica de negocio y envío de correos.
* **Dashboarding:** 

### Modelo de Estados (Autómata Finito de la Adecuación)
El ciclo de vida de la solicitud se modela mediante las siguientes transiciones de estado para evitar baches operativos:

`[Creada]` ➔ `[Notificación Enviada al Docente]` ➔ `[Confirmada por Docente]` ➔ `[Implementada]` ➔ `[Evaluada en Encuesta]`

## Modelo Entidad-Relación (Borrador)
El diseño lógico de la base de datos prioriza la anonimización y la integridad referencial:

* `Estudiantes` (Datos demográficos y académicos)
* `Adecuaciones_Catalogo` (Tipos de apoyo disponibles)
* `Solicitudes` (Instancia de asignación de una adecuación)
* `Docentes_Notificaciones` (Registro de trazabilidad y tokens de confirmación)
* `Encuestas_Satisfaccion` (Feedback histórico vinculado a la solicitud)
 ![Modelo Relacional de Base de Datos](docs/diagrama_bd.png)
---
*Boceto conceptual*
