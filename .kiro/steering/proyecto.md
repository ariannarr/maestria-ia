# Contexto del proyecto

Este repositorio guarda ejercicios, proyectos e información de la asignatura
**Introducción a la Inteligencia Artificial** de la **Maestría en Inteligencia
Artificial** de la Facultad de Matemáticas (FMAT) de la **UADY**.

- **Autora:** Arianna Rodríguez Rodas
- **Profesor:** Dr. Víctor Uc Cetina
- **Modalidad:** Presencial
- **Entrega:** Todo el trabajo vive en este repositorio de GitHub y funciona
  como portafolio digital evaluable.

## Estructura del repositorio

- `Curso/` — Información de la asignatura y planeación didáctica. Es material de
  referencia; normalmente no se modifica.
- `README.md` — Descripción general del repositorio.
- `tareas/` — Una carpeta por tema. Cada tema agrupa sus ejercicios.
  - Ejemplos: `tareas/Agentes/Ejercicio 1/`, `tareas/Conceptos básicos de
    Inteligencia Artificial/ejercicios/`.
  - Dentro de un ejercicio conviven el `Entregable.md`, el código en `project/`
    y las salidas en `evidencias/`.

## Convenciones de organización

- Crea **una carpeta por ejercicio**. No mezcles entregables de temas distintos.
- El reporte principal de cada ejercicio se llama `Entregable.md`.
- El código de un ejercicio va en una subcarpeta `project/` (con `config/`,
  `src/`, etc. según aplique).
- Las salidas, capturas y logs van en `evidencias/`.
  - Capturas de pantalla como `evidencia_01.png`, `evidencia_02.png`, ...
  - Logs de ejecución como `01.txt`, `02.txt`, ... con nombre descriptivo
    cuando aporte contexto (por ejemplo `03_prueba_acercar_P.txt`).
- Los retos opcionales van en una subcarpeta `evidencias/reto_opcional/`.
- Usa rutas relativas en los enlaces de los `Entregable.md` para que funcionen
  dentro de GitHub.

## Al crear un ejercicio nuevo

1. Confirma el tema y crea la carpeta bajo `tareas/<Tema>/`.
2. Coloca el enunciado o las indicaciones dentro del propio `Entregable.md`.
3. Si hay código, ponlo en `project/` y documenta cómo ejecutarlo.
4. Guarda toda evidencia reproducible en `evidencias/`.
