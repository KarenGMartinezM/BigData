Análisis del Límite de Precisión del 90% en el Modelo LeNet
Observaciones
Durante el entrenamiento del modelo LeNet para el reconocimiento de dígitos del conjunto de datos MNIST, se observó un comportamiento recurrente: la precisión del modelo se estabilizó en torno al 90% sin mejorar a pesar de diversas modificaciones. Este límite plantea preguntas sobre las limitaciones del modelo y las posibles razones detrás de este estancamiento.
1.	Arquitectura del modelo:
o	El modelo LeNet es una arquitectura clásica, diseñada originalmente para tareas menos complejas. Aunque es adecuada para el reconocimiento básico de patrones en MNIST, su capacidad para generalizar está limitada debido a su simplicidad.
o	Incluye dos capas convolucionales seguidas de capas de agrupamiento (pooling) y capas densas totalmente conectadas. Esta estructura, aunque funcional, puede ser insuficiente para aprender patrones más complejos en los datos.
2.	Configuración del entrenamiento:
o	Se utilizó un optimizador SGD (Descenso por Gradiente Estocástico) con una tasa de aprendizaje fija. Este optimizador no ajusta dinámicamente la tasa de aprendizaje, lo que puede dificultar que el modelo escape de mínimos locales y alcance mejores resultados.
o	La cantidad de épocas se incrementó para dar más tiempo al modelo para aprender. Sin embargo, no se observaron mejoras significativas en la precisión más allá del 90%.
3.	Funciones de activación:
o	Inicialmente se empleó la función de activación tanh en las capas convolucionales y densas. Al cambiarla por ReLU, se esperaba mitigar el problema del desvanecimiento del gradiente, pero el cambio no produjo mejoras significativas en la precisión final.
4.	Capacidad del modelo:
o	Aumentar la profundidad del modelo agregando más capas convolucionales y densas tampoco logró superar el límite del 90%, lo que sugiere que la limitación no está únicamente relacionada con la complejidad estructural del modelo.
Suposiciones
1.	Modelo simple: La simplicidad de la arquitectura LeNet puede ser una razón clave por la cual el modelo no logra superar el 90% de precisión. Redes más avanzadas podrían ser necesarias para capturar patrones más sutiles.
2.	Optimizador: La utilización del optimizador SGD, que no ajusta su tasa de aprendizaje, podría estar contribuyendo al estancamiento. Optimizadores como Adam podrían ofrecer mejores resultados al adaptarse dinámicamente durante el entrenamiento.
3.	Regularización insuficiente: La falta de capas como Dropout entre las capas convolucionales y densas podría estar limitando la capacidad del modelo para generalizar correctamente y evitar el sobreajuste.
4.	Patrones complejos: La naturaleza de los datos MNIST puede requerir modelos con mayor capacidad para capturar representaciones complejas, algo que LeNet, en su implementación original, no logra.
Propuestas de Mejora
Para superar el límite de precisión del 90%, se sugieren las siguientes estrategias:
1.	Cambios en la arquitectura:
o	Agregar más capas convolucionales y densas para aumentar la capacidad del modelo.
o	Introducir capas Dropout para mejorar la generalización y evitar el sobreajuste.
o	Incrementar el número de filtros en las capas convolucionales.
2.	Optimizador avanzado:
o	Utilizar Adam en lugar de SGD para permitir una adaptación dinámica de la tasa de aprendizaje y acelerar la convergencia.
3.	Funciones de activación:
o	Usar ReLU en lugar de tanh para mitigar el desvanecimiento del gradiente y facilitar un aprendizaje más efectivo.
4.	Técnicas de regularización:
o	Implementar Data Augmentation para incrementar la variabilidad en los datos de entrenamiento.
o	Aplicar capas Batch Normalization para estabilizar y acelerar el entrenamiento.
5.	Redes avanzadas:
o	Explorar arquitecturas modernas como ResNet o DenseNet que han demostrado ser eficaces en tareas de clasificación complejas.
o	Probar aprendizaje transferido utilizando modelos preentrenados.
6.	Incremento de épocas:
o	Aumentar el número de épocas para dar más tiempo al modelo para aprender patrones complejos.
Con estas estrategias, se espera que el modelo pueda superar el límite observado del 90% y alcanzar un mejor desempeño en la tarea de clasificación de dígitos del conjunto de datos MNIST.
