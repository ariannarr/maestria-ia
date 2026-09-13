# Este reporte corresponde a la tarea: Perceptrón multicapa -> Ejercicio 1.

## Elaborado por: Arianna Rodríguez Rodas

### 1. Enlaces de Colab (o archivos .ipynb) de las dos notebooks modificadas, con las corridas originales y las profundas.

NumPy: [04 Multilayer perceptron.ipynb](https://colab.research.google.com/drive/19tdSWjUyD3flCnyNKZS242x2PyNYFftm?usp=sharing)

Keras: [05 Keras - multilayer perceptron - iris.ipynb](https://colab.research.google.com/drive/1hoJihGNNiZu6kGyUbmmLdQsyQF3gnyxE?usp=sharing)

### 2. Capturas: curvas de error/pérdida de las cuatro corridas y los dos model.summary() de Keras.

**Keras**

Original:

Gráfica loss

![Gráfica loss](evidencias/Ejecuciones%20originales/keras-grafica-loss-original.png)

model.summary()

![Keras model summary original](evidencias/Ejecuciones%20originales/keras-model-summary-original.png)


Profunda:

Gráfica loss

![Gráfica loss profunda](evidencias/Ejecuciones%20profundas/keras-grafica-loss-profunda.png)

model.summary()

![Keras model summary profunda](evidencias/Ejecuciones%20profundas/keras-model-summary-profunda.png)


**NumPy**

Original:

Gráfica de error (error final ≈ 0.0571)

![NumPy gráfica error original](evidencias/Ejecuciones%20originales/numpy-grafica-loss-original.png)

Profunda:

Gráfica de error (error final ≈ 0.0820)

![NumPy gráfica error profunda](evidencias/Ejecuciones%20profundas/numpy-grafica-loss-profunda.png)


### 3. Reporte

**Observaciones:** Para la NumPy de 4 capas hice un ajuste de código para que apuntara a las neuronas y posiciones correctas. Ej:

      for j in range(num_neurons_layer4_deep):
        weighted_delta_errors += layer4_deep[j][i+1] * delta_layer4_deep[j]

Dejé `layer4_deep[j][i+1]` en lugar de `layer4_deep[i][j+1]`, no modifiqué esa sección en el original.

**¿Bajar más el error al añadir dos capas, o se estancó / empeoró? ¿Igual en NumPy y en Keras?**

En NumPy, la ejecución con 4 capas no fue suficiente para obtener un mejor resultado, de hecho, con 500 epochs da un resultado ligeramente superior que la ejecución con 2 capas, o sea que empeoró, sin embargo, la gráfica muestra que sí va aprendiendo y sigue bajando. No se identifica un estancamiento 100%, se estanca por un tiempo y luego vuelve a bajar. En la ejecución con 2 capas se estanca, en la gráfica se nota cómo va bajando pero a partir de la época 200 ya no desciende tanto. 

En Keras, añadir 2 capas empeoró y se estancó, mientras que con 2 capas la curva muestra que puede ir mejorando, al ejecutarlo con 4 capas no bajó, en el caso de 4 capas se estancó al llegar a aproximadamente a las 200 épocas, no hubo mucha mejora de la 300 en adelante, dando como resultado un estancamiento sin haber bajado más que la original. En esta identifiqué que los valores de inicialización afectan la curvatura de la gráfica con 2 capas, a veces tiene bastante caída y otras no tanto como en la captura que dejé. 

No es igual en NumPy y en Keras, una de las diferencias significativas es que en NumPy con 4 capas sí se identifica que va aprendiendo.

**¿Las curvas de la notebook 01 y de Keras se parecen con la misma topología? Si no, ¿qué diferencias de implementación podrían explicarlo (orden de los datos, inicialización, vectorización, etc.)?**

notebook 01 = NumPy

No se parecen exactamente. En NumPy la gráfica tiene mesetas, puede verse cómo cae y se aplana y nuevamente cae, este comportamiento no lo tiene Keras. Las gráficas de NumPy bajan más que las de Keras. En ambos casos, agregar capas no ayudó.

Las diferencias que podrían explicarlo son: la inicialización de pesos distinta, NumPy usa generate_weights con rand-0.5, el orden de la matriz de pesos de NumPy.

**Con sigmoides apiladas y MSE, ¿tiene sentido que una red más profunda no aprenda mejor en Iris? Relaciónalo con lo que viste en las gráficas.**

Correcto, no aprende mejor porque Iris es pequeño y casi separable, no necesita profundidad. Las sigmoides apiladas provocan el gradiente que se desvanece, como se puede observar en las gráficas con las mesetas de NumPy y el estancamiento de Keras. En este caso, agregar más capas no da beneficio, solo lo vuelve más difícil de entrenar.


### 4. Evidencias de ejecución en Colab (entorno de ejecución)

**Keras**

Original:

![Keras entorno de ejecución original](evidencias/Ejecuciones%20originales/keras-ejecucion-en-colab-original.png)

Profunda:

![Keras entorno de ejecución profunda](evidencias/Ejecuciones%20profundas/keras-ejecucion-en-colab-profunda.png)

**NumPy**

Original:

![NumPy entorno de ejecución original](evidencias/Ejecuciones%20originales/numpy-ejecucion-en-colab-original.png)

Profunda:

![NumPy entorno de ejecución profunda](evidencias/Ejecuciones%20profundas/numpy-ejecucion-en-colab-profunda.png)
