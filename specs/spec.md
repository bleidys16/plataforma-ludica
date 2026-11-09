# Especificación

## Contexto

Proyecto de Bleidys Paola Larios Torregrossa para el curso **Lógica y programación**.
La plataforma está dirigida a niños de 6 a 12 años y propone retos visuales para
practicar secuencias, patrones y algoritmos sencillos (avanzar, girar y repetir).
El docente acompaña el trabajo y consulta el desempeño; el niño participa con un código
de clase y un avatar, sin correo electrónico.

## Historias de usuario

### H1. Resolver retos y mejorar

Como estudiante, quiero resolver un reto y poder repetirlo, para practicar y mejorar mi
resultado sin perder mis avances anteriores.

**Criterios de aceptación**

- Cada intento válido registra los aciertos, el total de preguntas, las estrellas
  obtenidas y su fecha.
- Al terminar la actividad, el estudiante recibe de 1 a 3 estrellas con animación y
  sonido. Pocas respuestas correctas otorgan 1 estrella; una actividad sin errores
  otorga 3. El criterio exacto para 2 estrellas queda pendiente porque el encargo no lo
  especifica.
- Repetir una actividad conserva los intentos anteriores; el progreso de esa actividad
  usa la mejor puntuación obtenida.
- El total de estrellas del estudiante suma su mejor puntuación en cada actividad, no
  todos los intentos, para que repetir no duplique estrellas sin mejorar.
- El estudiante puede ver el total de estrellas reunidas.

### H2. Consultar el progreso de la clase

Como docente, quiero consultar estrellas y repeticiones por actividad, para identificar
qué retos necesitan refuerzo.

**Criterios de aceptación**

- El docente puede consultar las estrellas de cada estudiante por actividad, cuáles
  actividades se repiten con mayor frecuencia y cuántas repeticiones tiene cada una.
- Los resultados agregados no exponen datos personales innecesarios de los niños.

## Requisitos funcionales

| Código | Requisito | Historia |
| --- | --- | --- |
| RF1 | Registrar cada intento con estudiante, actividad, aciertos, total y fecha. | H1 |
| RF2 | Calcular entre 1 y 3 estrellas por intento mediante una regla configurable. | H1 |
| RF3 | Conservar el historial y calcular el mejor resultado por estudiante y actividad. | H1 |
| RF4 | Calcular el total de estrellas como la suma de los mejores resultados por actividad. | H1 |
| RF5 | Proveer métricas agregadas de estrellas e intentos para el docente. | H2 |

## Requisitos no funcionales

| Código | Requisito | Cómo se verifica |
| --- | --- | --- |
| RNF1 | Mantener separación entre rutas, servicios y modelos. | Pruebas y revisión de estructura |
| RNF2 | No almacenar correo de estudiantes menores. | Revisión del modelo de estudiante |
| RNF3 | Validar límites del intento antes de persistirlo. | Pruebas de servicio para entradas inválidas |

## Casos límite

- Rechazar intentos con total de preguntas menor o igual a cero, aciertos negativos o
  aciertos mayores que el total.
- Un estudiante sin intentos tiene cero estrellas acumuladas.
- Un nuevo intento con menos estrellas no reduce el mejor resultado previo.
- No contar el primer intento como repetición.

## Fuera de alcance

- Autenticación y autorización completas para docentes y estudiantes.
- Definición pedagógica final de los umbrales de estrellas.
- Despliegue público y URL de Render hasta completar la publicación.

## Criterios de terminado

- La regla de estrellas está acordada y cubierta con pruebas de límites.
- Los servicios calculan progreso y métricas sin trasladar reglas de negocio a las rutas.
- `pytest -v` y `ruff check .` pasan.

## Dudas abiertas

| Duda | Respuesta del cliente |
| --- | --- |
| ¿Qué criterio exacto otorga 2 estrellas? | El encargo solo define que pocas respuestas correctas dan 1 y que una actividad sin errores da 3; pendiente de aclaración. |
