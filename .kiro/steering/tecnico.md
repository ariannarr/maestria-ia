# Entorno técnico y buenas prácticas

## Stack de la asignatura

- **Lenguaje:** Python 3.10+.
- **Bibliotecas base:** NumPy, scikit-learn, Matplotlib, NetworkX, pgmpy.
- **Aprendizaje profundo / visión / refuerzo:** PyTorch o TensorFlow/Keras,
  OpenCV, Gymnasium.
- **LLMs / RAG:** API de OpenAI u otras APIs de LLM, Hugging Face Transformers,
  LangChain.
- **Entorno:** Jupyter Notebook/JupyterLab o VS Code con la extensión de Python.
- **Datasets:** UCI ML Repository, Kaggle, OpenML.

Usa preferentemente estas herramientas antes de introducir dependencias nuevas.
Si un ejercicio necesita otra biblioteca, justifícalo en el `Entregable.md`.

## Buenas prácticas de código

- Escribe código **reproducible**: fija semillas aleatorias cuando el resultado
  dependa del azar y documenta cómo ejecutarlo.
- Prefiere configuración en archivos (por ejemplo `.yaml`) sobre valores fijos
  en el código cuando el ejercicio explore varios escenarios, como ya se hace en
  `Agentes/Ejercicio 1/project/config/`.
- Comenta el código en español, explicando el *por qué* de las decisiones, no
  solo el *qué*.
- Mantén los ejercicios autocontenidos dentro de su carpeta `project/`.

## Ejecución y evidencias

- Al ejecutar experimentos, **guarda la salida** en `evidencias/` (logs `.txt` y
  capturas `.png`) para que el resultado sea verificable.
- Nombra los archivos de evidencia de forma que se relacionen con el paso o el
  agente que documentan.
- Antes de dar por terminado un ejercicio, verifica que el código corre y que la
  evidencia enlazada en el `Entregable.md` existe y es coherente con lo
  reportado.

## Entorno de trabajo (Windows / PowerShell)

- El sistema es Windows con PowerShell. Adapta los comandos: usa `;` en vez de
  `&&`, `Get-ChildItem` en vez de `ls`, y variables como `$env:USERPROFILE`.
- No inicies procesos de larga duración (servidores, watchers) desde comandos
  automáticos; indícalos para ejecución manual.
