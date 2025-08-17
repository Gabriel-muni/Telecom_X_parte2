# Telecom_X_parte2
Análisis de Churn de Clientes
Descripción del Proyecto
Este proyecto realiza un análisis exploratorio y modelado predictivo para identificar los factores que influyen en la rotación (churn) de clientes en la empresa de telecomunicaciones Telecom X. El objetivo es construir modelos que permitan predecir qué clientes son propensos a abandonar el servicio.

Origen de Datos
Los datos utilizados en este análisis provienen del archivo df_limpo.csv. Este archivo contiene información detallada sobre los clientes, incluyendo datos demográficos, servicios contratados, información de cuenta y estado de churn entre otros.

Análisis y Preprocesamiento de Datos
1. Carga de Datos: Los datos se cargaron utilizando la librería pandas.
2. Exploración Inicial: Se realizó una exploración inicial para entender la estructura de los datos, tipos de variables y presencia de valores nulos.
3. Limpieza de Datos: Se eliminó la columna customerID ya que no es relevante para el análisis predictivo. Se imputaron los valores nulos en las columnas Total.Day y account.Charges.Total eliminando las filas correspondientes.
4. Codificación de Variables Categóricas: Las variables categóricas se transformaron utilizando One-Hot Encoding para ser utilizadas en los modelos. Se manejaron los casos de variables con tres categorías (Sí, No, No service) reemplazando "No internet service" por "No" antes de la codificación.
5. Análisis de Correlación: Se calculó la matriz de correlación para visualizar la relación entre las variables, prestando especial atención a la correlación con la variable objetivo (Churn_Yes). Se visualizó una matriz filtrada con variables que tienen una correlación absoluta mayor o igual a 0.2 con la variable objetivo.
6. Análisis de Multicolinealidad (VIF): Se realizó un análisis del Factor de Inflación de Varianza (VIF) para identificar y mitigar la multicolinealidad entre las variables predictoras. Se eliminaron columnas con VIF alto (phone.PhoneService_Yes, phone.MultipleLines_No phone service, Total.Day, internet.InternetService_No, account.Charges.Total) para mejorar la estabilidad del modelo.
7. Escalado de Datos: Las variables numéricas fueron escaladas utilizando StandardScaler para asegurar que tengan una media de 0 y una desviación estándar de 1, lo cual es importante para algunos modelos.
8. Balanceo de Clases: Dado que el conjunto de datos de churn suele estar desbalanceado (menos clientes que abandonan que los que no), se aplicó la técnica SMOTE (Synthetic Minority Over-sampling Technique) en el conjunto de entrenamiento para crear instancias sintéticas de la clase minoritaria y balancear el dataset.
## Modelado Predictivo
Se entrenaron dos modelos de clasificación para predecir el churn de clientes:

*Regresión Logística: Un modelo lineal que estima la probabilidad de que un cliente abandone el servicio.

*Random Forest Classifier: Un modelo de conjunto basado en árboles de decisión que puede capturar interacciones no lineales entre las variables.

Ambos modelos se entrenaron con el conjunto de datos balanceado (resultado de aplicar SMOTE) y se evaluaron en el conjunto de prueba original (no balanceado) para obtener métricas de rendimiento realistas.

## Evaluación de Modelos
La evaluación de los modelos se basó en las siguientes métricas:

*Accuracy (Precisión General): Proporción de predicciones correctas.

*ROC AUC (Área bajo la Curva ROC): Mide la capacidad del modelo para distinguir entre las clases. Un valor más alto indica una mejor capacidad discriminatoria.

*Confusion Matrix: Tabla que resume el número de predicciones correctas e incorrectas para cada clase.

*Classification Report: Proporciona métricas clave como Precisión, Recall (Sensibilidad), F1-score y soporte para cada clase.

Los resultados de la evaluación mostraron que ambos modelos tienen un rendimiento razonable. La Regresión Logística tuvo un ROC AUC ligeramente más alto, mientras que el Random Forest tuvo una mayor precisión general. 

La elección del modelo final dependerá de las prioridades del negocio (por ejemplo, si es más importante minimizar los falsos negativos o los falsos positivos).
