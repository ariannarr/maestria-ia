# Este reporte corresponde a la tarea: Agentes -> Ejercicio 1.

## Elaborado por: Arianna Rodríguez Rodas

## 1. Archivo config/mi_cueva_4x4.yaml
[Cueva 4x4](project\config\mi_cueva_4x4.yaml)

## 2. Diagrama de la cueva:
![Diagrama de la cueva](evidencias\evidencia_01.png)

[Diagrama en txt](evidencias\01.txt)

## 3. Breve reporte

### ¿Qué agentes lograron salir con el oro en tu mapa y cuáles no?
* Agentes que lograron salir (1): 06_learning_agent.py. Solo este agente pudo lograrlo debido a su capacidad para aprender y reforzar con las épocas ejecutadas.
* Agentes que no lograron salir (4): 02_simple_reflex_agent.py, 03_model_based_agent.py, 04_goal_based_agent.py y 05_utility_based_agent.py. Todos estos agentes terminaron ciclados en algún punto, excepto el `05_utility_based_agent.py` que terminó muerto al ser comido por el Wumpus.

### ¿Por qué el agente de reflejo simple falla (o tiene suerte) en tu diseño?
* El agente de reflejo simple falla en mi diseño porque al toparse con el primer hedor en la posición 3,1 se queda ciclado mientras ejecuta el proceso de movimiento que conoce. No hubo ninguna configuración donde no fallara.
* Hice una prueba con otra configuración que lo lleva directo a tomar el oro, pero al toparse con una brisa, nuevamente se queda ciclado y no sale de la cueva, siempre va hacia adelante e izquierda y se cicla, el mundo configurado es: [Cueva fácil](evidencias\arianna_classic_4x4_gold_asegurado.txt)

### ¿Cómo cambia el resultado del agente basado en modelo si acercas o alejas un pit de la casilla inicial?
* El agente se quedó ciclado en la casilla 1,1 al acercar el pit. Inicialmente ningún P estaba cerca, pero al acercarlo, la casilla del agente quedó con Percept [Breeze] y eso hizo que se ciclara. De igual manera se cicla si alejo otros pits.
Evidencia de ejecución: [Acercar P ejecución](evidencias\03_prueba_acercar_P.txt)

## 4. Evidencias de la ejecución de los agentes
[02_simple_reflex ejecución](evidencias\02.txt)

![02_simple_reflex](evidencias\evidencia_02.png)

[03_model_based ejecución](evidencias\03.txt)

![03_model_based](evidencias\evidencia_03.png)

[04_goal_based ejecución](evidencias\04.txt)

![04_goal_based](evidencias\evidencia_04.png)

[05_utility_based ejecución](evidencias\05.txt)

![05_utility_based](evidencias\evidencia_05.png)

[06_learning ejecución](evidencias\06.txt)

![06_learning](evidencias\evidencia_06.png)

## 5. Reto opcional

Después de varios intentos de configuración donde el agente no disparaba, tras hacer varias ejecuciones con diferentes configuraciones, me puse a investigar el código con apoyo de la IA y pudimos identificar la propiedad "walls", esta sí permite bloquear el paso pero sin dejar un Percept en las celdas adyacentes, con esto el agente ya puede identificar una única casilla para el Wumpus, le dispara y puede ir por el oro.

La cueva que me funcionó:
[Cueva difícil 4x4 con 1 wall](project\config\mi_cueva_dificil_4x4.yaml)
```text
4 | P  P  #  G
3 | P  .  .  W
2 | .  .  .  .
1 | >  .  .  .
    1  2  3  4
```

Resultado de la ejecución: [Cueva difícil 4x4 con 1 wall ejecución](evidencias\reto_opcional\04_dificil_dispara.txt)

Esta es una de las cuevas que confuguré y no funcionó, el agente se quedó ciclado:
[Cueva difícil 4x4](project\config\mi_cueva_dificil_4x4_no_shoot.yaml)
```text
4 | P  P  P  G
3 | .  .  .  W
2 | .  .  .  .
1 | >  .  .  .
    1  2  3  4
```


Las evidencias de ejecución:
[Evidencias de ejecución](evidencias\reto_opcional\\)

Ejecuté los agentes `03_model_based_agent` y `04_goal_based_agent`, ninguno trajo el oro con esta configuración, el agente `04_goal_based_agent` no disparó, se cicló también.

En este escenario solo el agente `05_utility_based_agent` obtuvo el oro.

El agente `06_learning_agent` tampoco obtiene el oro.

Probé varias configuraciones más donde incluyo 3 pits pero 0 walls, en ninguna dispara el `04_goal_based_agent`,

### Conclusión del reto
Es necesario configurar al menos 1 wall y evitar que los pits y su brisa estén dentro de las casillas que se esperan que el agente lea como "seguras". De esta manera, el agente puede ubicar una única casilla para el Wumpus y le dispara para abrirse paso hacia el Gold.