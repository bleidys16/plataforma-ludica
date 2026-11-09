# AGENTS.md

Contexto del proyecto para los agentes de IA. Léalo antes de cualquier cambio.

## Proyecto

Plataforma web lúdica para niños de 6 a 12 años. Curso: Lógica y programación, con
retos visuales de secuencias, patrones y algoritmos sencillos: avanzar, girar y repetir.
Mecánica: Estrellas, de 1 a 3 por aciertos; se permiten reintentos para mejorar.
Roles: docente y niño. El niño entra con código de clase y avatar, sin correo.

## Stack

- Python 3.11 o superior, FastAPI y plantillas Jinja2.
- SQLModel; SQLite en desarrollo y PostgreSQL al publicar.
- pytest con TestClient y Ruff.
- GitHub Actions para CI y Render para el despliegue.

## Comandos

- Instalar: `pip install -r requirements-dev.txt`
- Ejecutar: `uvicorn app.main:app --reload`
- Pruebas: `pytest -v`
- Estilo: `ruff check .`

## Estructura

- `app/rutas/`: reciben solicitudes y llaman a servicios; sin reglas de negocio.
- `app/servicios/`: reglas de negocio, con pruebas propias.
- `app/modelos/`: tablas SQLModel.
- `app/templates/` y `app/static/`: interfaz y PWA.
- `tests/`: pruebas; `tests/aceptacion/`: criterios de la especificación.
- `app/proyecto.py`: datos del proyecto y URL pública.

## Convenciones

- Usar nombres en español, claros y completos.
- Hacer cambios pequeños, una tarea por rama, y probar antes del código.
- Al iniciar cada sesión, leer `STATE.md`.

## Qué no hacer

- No escribir claves ni contraseñas en el código; leerlas de variables de entorno.
- No instalar dependencias sin verificar que existen en pypi.org.
- No modificar ni borrar pruebas para que pasen.
- No usar datos personales reales de niños.
- No hacer commit ni push: los hace el desarrollador.

## Lecciones aprendidas

Cada vez que el agente se equivoque, escriba aquí una regla para evitar repetir el error.
