# NLP - Desafío 3: Modelo de Lenguaje a Nivel de Caracteres

Este repositorio contiene la resolución del **Desafío 3** de la asignatura Procesamiento de Lenguaje Natural I (CEIA - FIUBA). El objetivo central de este proyecto es construir y comparar distintas arquitecturas de Redes Neuronales Recurrentes (RNN) para generar texto imitando el estilo del autor Julio Verne a nivel de **caracteres individuales**.

## 🚀 Objetivo del Desafío

A diferencia de los modelos basados en tokens de palabras (como *Word2Vec*), aquí la red neuronal desconoce el significado semántico del texto y aprende puramente la **distribución estadística, sintaxis y morfología** iterando carácter por carácter.

Se entrena al modelo para predecir el próximo carácter de una secuencia dada, permitiéndole generar desde cero palabras válidas, signos de puntuación de diálogo e incluso neologismos.

## 🛠️ Tecnologías y Metodología

- **Corpus Utilizado**: `corpus_JulioVerne.txt` (Traducción al español de "Viaje al Centro de la Tierra").
- **Framework**: TensorFlow / Keras.
- **Arquitecturas Evaluadas**: 
  - `SimpleRNN` (Línea base).
  - `LSTM` y `GRU` (Celdas avanzadas con compuertas para dependencias a largo alcance).
- **Métrica de Evaluación**: Perplejidad en conjunto de validación mediante `PplCallback`.
- **Estructuración del Dataset**: Formato *many-to-many* utilizando secuencias continuas de longitud fija (100 caracteres).

## 🧠 Estrategias de Generación de Texto Exploradas

A partir del mejor modelo entrenado (GRU), se experimentó con tres métodos de generación a partir de una oración inicial o semilla:

1. **Greedy Search**: Muestreo determinístico que converge a los patrones de mayor probabilidad, ilustrando el problema de caer en bucles repetitivos.
2. **Beam Search Determinístico**: Mantenimiento de múltiples hipótesis en paralelo, mejorando la coherencia y respetando fuertemente el estilo de puntuación del autor original.
3. **Beam Search Estocástico y Temperatura**: Muestreo probabilístico. Modulando el parámetro de "Temperatura" se controla el equilibrio termodinámico entre adherirse a secuencias conocidas ($T \leq 1.0$) y potenciar una creatividad extrema a expensas de la corrección gramatical y sintáctica ($T > 1.0$).

## 📂 Uso y Ejecución

El archivo central es el Jupyter Notebook (`desafio_3_JulioVerne.ipynb`), el cual está estructurado, comentado y preparado para ejecutarse de manera fluida y de principio a fin desde entornos con soporte de GPU como **Google Colab**. Incluye rutinas para autodescarga o carga manual segura del corpus según el entorno.