# Estado del proyecto

## Estado actual

Repositorio publicado en GitHub. El último CI de `main` terminó correctamente.
La aplicación está desplegada en Render en https://plataforma-ludica-xe2a.onrender.com;
la página de inicio, `/salud` y `/docs` respondieron correctamente el 2026-11-09.

## Decisiones

| Fecha | Decisión | Motivo |
| --- | --- | --- |
| 2026-11-09 | Separar las rutas HTTP de las reglas de negocio y los modelos | El plan técnico define las capas `app/rutas/`, `app/servicios/` y `app/modelos/` para mantener responsabilidades claras. |

## Siguiente paso

Definir y acordar el umbral para otorgar 2 estrellas; después, implementar los modelos
SQLModel de estudiantes, actividades e intentos con sus pruebas.
