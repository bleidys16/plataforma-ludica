# Plataforma lúdica: Lógica y programación

Plataforma web lúdica para que niños de 6 a 12 años practiquen lógica y programación
mediante retos visuales de secuencias, patrones y algoritmos sencillos, como avanzar,
girar y repetir. La mecánica asignada es **Estrellas**: cada actividad otorga de 1 a 3
estrellas según los aciertos; el estudiante puede repetirla para mejorar su resultado.

- **Aprendiz:** Bleidys Paola Larios Torregrosa
- **Curso:** Lógica y programación
- **Mecánica:** Estrellas
- **Aplicación publicada:** https://plataforma-ludica-xe2a.onrender.com

La plantilla actual expone la página de inicio, el estado del servicio y la documentación
de la API. El registro de estudiantes, actividades, intentos y estrellas es el siguiente
incremento del producto; consulta el diseño propuesto en [`specs/plan.md`](specs/plan.md).

## Ejecutar en su equipo

En Windows:

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements-dev.txt
uvicorn app.main:app --reload
```

En Linux o macOS, cree el entorno con `python3 -m venv .venv` y actívelo con `source .venv/bin/activate`.

Abra http://127.0.0.1:8000 en el navegador. La documentación de la API está en http://127.0.0.1:8000/docs.

## Verificar

```bash
pytest -v
ruff check .
```

## Estructura

| Carpeta o archivo | Contenido |
| --- | --- |
| `app/` | Aplicación FastAPI: rutas, servicios, modelos, plantillas y archivos estáticos |
| `app/proyecto.py` | Datos de identificación del proyecto |
| `tests/` | Pruebas automatizadas |
| `specs/` | Especificación, flujo de usuario, plan técnico, tareas y decisiones |
| `prompts/` | Prompts versionados |
| `entregas/` | Respuestas semanales; `entregar.py` genera el PDF |
| `AGENTS.md` | Contexto del proyecto para los agentes de IA |
| `STATE.md` | Estado, decisiones y siguiente paso |
| `render.yaml` | Configuración del despliegue en Render |

## Diseño de la mecánica

Cada intento debe conservar sus aciertos, total de preguntas, estrellas y fecha. Para el
progreso se toma la mejor cantidad de estrellas lograda en cada actividad, y el total
del estudiante suma esas mejores puntuaciones; así, repetir permite mejorar sin borrar
el historial ni penalizar el progreso. Los umbrales exactos para asignar 1, 2 o 3
estrellas deben definirse antes de implementar el servicio.

## Licencia

MIT. Consulte el archivo LICENSE.
