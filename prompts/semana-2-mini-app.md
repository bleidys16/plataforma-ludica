# Mini-aplicación de práctica: Lista de tareas

## Versión A
**Objetivo:** construir la mini-aplicación con un prompt de una línea.

**Herramienta y modelo:** Copilot con el modelo GPT-4o.

**Prompt:**
```
Haz una app web de lista de tareas con FastAPI.
```

**Resultado:** La aplicación arranca, pero no cumple con la estructura requerida. Aprueba 0 de 7 pruebas de aceptación por inconsistencias en las rutas (creó /api/tasks en vez de /api/tareas) y genera 1 error de Ruff.

## Versión B
**Objetivo:** construir la misma aplicación con un prompt estructurado, AGENTS.md y pruebas de aceptación.

**Herramienta y modelo:** Copilot con el modelo GPT-4o.

**Prompt:**
```
## Rol
Actúa como desarrollador backend con experiencia en FastAPI, Jinja2 y pruebas con pytest.
## Objetivo
Construir la mini-aplicación web Lista de tareas con estos requisitos:
1. GET / muestra la lista de tareas, un formulario para agregar una tarea y, en cada
   tarea, botones para completarla y para eliminarla.
2. POST /api/tareas recibe {"titulo": "Estudiar FastAPI"} y responde con el código
   201 y la tarea creada: {"id": 1, "titulo": "Estudiar FastAPI", "completada": false}.
   El título debe tener entre 1 y 100 caracteres; si no, responde con el código 422.
3. GET /api/tareas devuelve la lista de tareas.
4. PUT /api/tareas/{id}/completar marca la tarea como completada y la devuelve.
5. DELETE /api/tareas/{id} elimina la tarea y responde con el código 204.
6. Si la tarea no existe, completar y eliminar responden con el código 404.
## Contexto
Lee AGENTS.md. El contrato de la API está en tests/test_aceptacion.py: las rutas, los nombres de los campos y los códigos de estado deben coincidir con esas pruebas.
## Restricciones
- Usa solo las dependencias de requirements.txt.
- Define las rutas en app/main.py y la lógica en app/servicios.py, sin importar
  FastAPI en servicios.
- Guarda los datos en memoria, sin base de datos ni archivos.
- No modifiques tests/test_aceptacion.py.
- La página usa HTML, CSS y JavaScript sin librerías externas.
## Formato de salida
Antes de escribir código, muestra el plan con las rutas completas de los archivos que vas a crear y espera mi aprobación. Al terminar, resume en una línea qué hace cada archivo.
## Ejemplo
POST /api/tareas con {"titulo": "Leer el encargo"} responde con el código 201 y devuelve:
{"id": 1, "titulo": "Leer el encargo", "completada": false}
PUT /api/tareas/1/completar devuelve:
{"id": 1, "titulo": "Leer el encargo", "completada": true}
## Criterio de éxito
python -m pytest -v pasa todas las pruebas y ruff check . no reporta errores. Si después de 3 intentos las pruebas no pasan, detente y explica el problema.
```

**Resultado:** La aplicación arranca y cumple los 6 requisitos solicitados. Aprueba 7 de 7 pruebas de aceptación tras 2 mensajes (solicitud y aprobación del plan) y no genera errores de Ruff (0 errores).

## Mejora
**Objetivo:** implementar el filtrado de tareas por estado y agregar botones para filtrar la lista en la página principal.

**Herramienta y modelo:** Copilot con el modelo GPT-4o.

**Prompt:**
```
## Rol
Actúa como desarrollador backend con experiencia en FastAPI, Jinja2 y pruebas con pytest.

## Objetivo
Implementar el filtrado de tareas por estado:
1. `GET /api/tareas` acepta el parámetro opcional `estado`.
2. Sin `estado`, devuelve todas las tareas.
3. `GET /api/tareas?estado=pendientes` devuelve solo las tareas cuyo campo `completada` es `false`.
4. `GET /api/tareas?estado=completadas` devuelve solo las tareas cuyo campo `completada` es `true`.
5. Si `estado` tiene cualquier otro valor, responde con el código 422.
6. La página principal ofrece los botones `Todas`, `Pendientes` y `Completadas`; al seleccionarlos, la lista visible corresponde al filtro elegido.
7. Añade `tests/test_mejora.py` con pruebas que comprueben los dos filtros y que un estado no válido devuelve 422.

## Contexto
Lee `AGENTS.md` y revisa la implementación actual antes de cambiarla. El contrato existente de la API está en `tests/test_aceptacion.py`; conserva sus rutas, campos y códigos de estado. La mejora se agrega a la aplicación Lista de tareas existente.

## Restricciones
- Usa solo las dependencias de `requirements.txt`; no instales dependencias.
- Define las rutas y la validación del parámetro en `app/main.py`.
- Implementa el filtrado de datos en `app/servicios.py`, sin importar FastAPI en ese módulo.
- Conserva el almacenamiento en memoria; no uses bases de datos ni archivos para los datos.
- No modifiques ni borres `tests/test_aceptacion.py`.
- La interfaz debe usar HTML, CSS y JavaScript sin librerías externas. Los tres botones deben filtrar usando la API y mostrar los resultados correspondientes.
- Conserva las funciones actuales para agregar, completar y eliminar tareas.

## Formato de salida
Antes de escribir código, muestra un plan con las rutas completas de todos los archivos que crearás o modificarás y espera mi aprobación. El plan debe indicar brevemente el cambio previsto en cada archivo No edites archivos antes de recibir la aprobación. Al terminar, resume en una línea qué hace cada archivo creado o modificado y muestra los resultados de las pruebas y del análisis de estilo.

## Ejemplo
Si existe esta tarea:
`{"id": 1, "titulo": "Leer el encargo", "completada": false}`

La petición `GET /api/tareas?estado=pendientes` responde con código 200 y:
`[{"id": 1, "titulo": "Leer el encargo", "completada": false}]`

La petición `GET /api/tareas?estado=otro` responde con código 422.

## Criterio de éxito
`python -m pytest -v` debe aprobar todas las pruebas, incluidas las de `tests/test_mejora.py`, y `ruff check .` no debe reportar errores. Si las pruebas o Ruff fallan, corrige el problema y vuelve a comprobarlo, hasta un máximo de 3 intentos; si después de 3 intentos siguen fallando, detente y explica el problema.
```

**Resultado:** Agregó el parámetro estado en GET /api/tareas y los botones de filtro en la página HTML. Todas las pruebas pasaron. No se registraron la cantidad exacta de pruebas ni el resultado de Ruff.

## Comparación
**Pruebas aprobadas:** Versión A (0/7) vs Versión B (7/7). Para la Mejora se informó que todas las pruebas pasaron, pero no se registró el total.

**Requisitos cumplidos:** Versión A (no determinado) vs Versión B (6/6). Para la Mejora no se registró un total de requisitos.

**Errores de Ruff:** Versión A (1) vs Versión B (0). El resultado de Ruff de la Mejora no se registró.

**Conclusión:**

El contrato de las pruebas y las restricciones del prompt B fueron clave para evitar que el agente improvisara. En la versión A, al darle una orden vaga, el agente usó SQLite y rutas en inglés (/api/tasks), lo que hizo fallar las pruebas de aceptación. Para la próxima vez, incluiré desde el inicio la estructura de archivos, el contrato exacto de la API y las restricciones visuales.
