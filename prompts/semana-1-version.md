# Semana 1: versión de la API

## Objetivo
Agregar el endpoint `GET /api/version` con su prueba.

## Herramienta y modelo
Copilot, modelo Auto.

## Prompt
Lee AGENTS.md. Agrega el endpoint GET/api/version, que devuelva la versión definidaen app/proyecto.py, con su prueba en tests/test_inicio.py. Antes de escribir código, explícame qué archivos vas a modificar y espera mi aprobación.

## Resultado
El agente modificó `app/rutas/api.py` para agregar el endpoint, que devuelve `proyecto.VERSION`, y `tests/test_inicio.py` para probarlo. Las 7 pruebas de `tests/test_inicio.py` pasaron. No fue necesario corregir el resultado.
