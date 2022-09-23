# Quiz 3: Medical-Cost-Personal

Quiz for my Datascience Class - using Kaggle´s Medical Cost Personal Dataset

# Requerimiento

1. A partir de el dataset [Medical Cost Personal Datasets](https://www.kaggle.com/datasets/mirichoi0218/insurance) construya un modelo de regresión lineal que busque minimizar el error de predicción en el costo de los seguros médicos.
2. Dentro del proceso tener en cuenta:
    *  Entrenar un modelo de regresión lineal sin aplicar ningún tipo de regularización. Evalúe dicho modelo y concluya.
        - ¿Es aceptable el error obtenido?
        - ¿Hay evidencia de overfitting?
    * Aplicar transformación polinomial a los datos de entrada y Regularización Ridge o Lasso al modelo de regresión. Probar con al menos 2 grados diferentes del polinomio y con al menos 3 valores de alpha para la regularización. Evalúe dichos modelos y concluir:
    * ¿Es posible mejorar el error? ¿ Qué hiperparámetros tiene el modelo que produce el menor error?
    * ¿Qué atributos parecen ser los más importantes para realizar la predicción

# Resumen de Solución

## Entrenamiento de regresión lineal sin regularización.

Se obtuvo un valor de MSE = 33596915.85136145. Es un valor alto, lo que indica un mal rendimiento al predecir el costo de los seguros médicos.
El mal rendimiento posiblemente es causado por un sobreajuste de los datos.

## Entrenamiento de regresión lineal con escalamiento de los datos usando minimax.

Se obtuvo un valor MSE = 0.008560069824175879. Lo cual simboliza un buen rendimiento y podría ser seleccionado, sin embargo, se procede a verificar si es posible optimizar el desempeño.

## Modelo Lasso

Se realizaron dos reducciones de dimensionalidad polinomial una con grado 2 y otra con grado 3. Además se realizaron 3 modelos Lasso en donde se ajustó sus hiperparámetro alpha en 0.1, 0.2 y 0.9, obteniendo los sigientes valores de MSE:

| Lasso     | Polynomial grado 2   | Polynomial grado 3         |
| --------- | -------------------- | --------------------       |
| **Alpha 0.1** | 0.03959177723052453 |   0.03959177723052453  |
| **Alpha 0.2** | 0.03959177723052453 | 0.03959177723052453   | 
| **Alpha 0.9** | 0.03959177723052453 | 0.03959177723052453   | 

El modelo lasso demuestra una mejora frente a la regresión lineal, sin embargo, se procede a verificar si es posible optimizar el desempeño. 
Vale la pena notar que de los hiperparámetros alpha que se usaron, estos no afectaron en la mejora del rendimiento del modelo.
## Modelo Ridge

Similar al modelo lasso, se realizó reducción de dimensionalidad polinomial, y se asignaron 3 valores de alpha a los modelos Ridge, 0.1, 0.2 y 0.9. Sus MSE son los siguientes:

| Ridge     | Polynomial grado 2   | Polynomial grado 3         |
| --------- | -------------------- | --------------------       |
| **Alpha 0.1** | 0.005275733981348491 |  0.005275733981348491  |
| **Alpha 0.2** | 0.005278511098625507 | 0.005278511098625507   | 
| **Alpha 0.9** | 0.0053639436121030405| 0.0053639436121030405   | 

Como se puede observar en la tabla, cambiar el hiperparámetro del modelo ridge, con los valores seleccionados, no afecta al desempeño. Sin embargo, el grado de la reducción polinomial si puede afectar el rendimiento del polinomio, al menos con los valores usados.

Este modelo, tiene el mejor rendimiento con los hiperparámetros de alpha en 0.1 y grado polinomial en 2.

# Conclusión

El modelo que tiene un mejor rendimiento para la predicción de costos de los seguros médicos es el modelo Ridge usando su hiperparámetro alpha ajustado en 0.1 y grado polinomial 2. Con un MSE de 0.005275733981348491.

