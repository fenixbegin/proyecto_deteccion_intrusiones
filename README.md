# CiberseguridadPROYECTO.ipynb: Detección de Intrusiones con Regresión Logística

Este proyecto utiliza un enfoque de regresión logística para detectar intrusiones cibernéticas basándose en el análisis del tráfico de red y el comportamiento del usuario. El objetivo es identificar patrones que indiquen actividades maliciosas dentro de una red.

## Datos

Los datos para este análisis se encuentran en el archivo `cybersecurity_intrusion_data.csv`. Este conjunto de datos contiene **9,537 registros** de actividad de red, con las siguientes características relevantes:

* `network_packet_size`: Tamaño de los paquetes de red.
* `protocol_type`: Tipo de protocolo de red utilizado (TCP, UDP, ICMP).
* `login_attempts`: Número de intentos de inicio de sesión.
* `session_duration`: Duración de la sesión.
* `encryption_used`: Tipo de cifrado utilizado (DES, AES).
* `ip_reputation_score`: Puntuación de reputación de la dirección IP.
* `failed_logins`: Número de intentos de inicio de sesión fallidos.
* `browser_type`: Tipo de navegador utilizado (Edge, Firefox, Chrome, Unknown).
* `unusual_time_access`: Indica si el acceso ocurrió en un horario inusual (0 o 1).
* `attack_detected`: Variable objetivo que indica si se detectó un ataque (0 o 1).

## Librerías Utilizadas

* `pandas`: Para manipulación y análisis de datos.
* `numpy`: Para operaciones numéricas.
* `matplotlib.pyplot`: Para visualización de datos.
* `seaborn`: Para visualizaciones estadísticas (matriz de confusión).
* `sklearn.impute.SimpleImputer`: Para manejar valores faltantes.
* `sklearn.linear_model.LogisticRegression`: Para el modelo de regresión logística.
* `sklearn.metrics.confusion_matrix`: Para evaluar el rendimiento del modelo.
* `sklearn.metrics.accuracy_score`: Para calcular la precisión del modelo.

## Preprocesamiento de Datos

* Se cargó el dataset `cybersecurity_intrusion_data.csv`.
* Se verificó la forma de los datos (9537 registros, 11 columnas) y la presencia de valores nulos.
* Los valores faltantes en la columna `encryption_used` fueron imputados utilizando la estrategia de la "moda" (el valor más frecuente).

## Análisis Exploratorio (Parcial)

Se realizó un análisis básico de cada característica en relación con la variable objetivo (`attack_detected`). Para las características numéricas, se identificaron el mínimo, promedio y máximo durante los ataques. Para las características categóricas, se identificó el valor más frecuente durante los ataques.

## Modelado

Se implementó un modelo de **regresión logística** para predecir si una sesión pertenece a la categoría de "ataque detectado" (1) o no (0).

* **Variable Dependiente (Y_train):** `attack_detected`
* **Variables Independientes (X_train):** `network_packet_size`, `login_attempts`, `session_duration`, `failed_logins`, `unusual_time_access`

El modelo de regresión logística fue entrenado utilizando las variables independientes seleccionadas y la variable dependiente.

## Evaluación del Modelo

Se evaluó el rendimiento del modelo de regresión logística utilizando una **matriz de confusión** y la métrica de **precisión**. La matriz de confusión visualiza el número de predicciones correctas e incorrectas para cada clase (ataque detectado o no detectado). La precisión calcula el porcentaje de predicciones correctas del modelo.
