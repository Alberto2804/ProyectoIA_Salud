# 🏥 Inteligencia Artificial Explicativa (XAI) en Salud

Este repositorio contiene el desarrollo práctico de dos modelos predictivos de Machine Learning aplicados al sector sanitario. El objetivo principal no es solo lograr predicciones precisas, sino aplicar técnicas de **Inteligencia Artificial Explicativa (XAI)** utilizando la librería SHAP para entender cómo y por qué los modelos toman sus decisiones.

## 📂 Estructura del Proyecto

* `datos_costes.csv y datos_ictus.csv`: Contienen los datasets originales utilizados para entrenar a los modelos (fuente: Kaggle).
* `/data_costes.ipynb y datos_ictus.ipynb`: Contienen los cuadernos de Python (Jupyter/Colab) con el preprocesamiento, entrenamiento y evaluación XAI.
* `README.md`: Explicación del enfoque y conclusiones del proyecto.

---

## 🔬 Caso de Uso 1: Modelo de Clasificación (Riesgo de Ictus)

**Objetivo:** Predecir si un paciente tiene riesgo de sufrir un ictus basándonos en su historial médico y estilo de vida.
**Dataset:** *Stroke Prediction Dataset* (Kaggle). Contiene datos de pacientes reales, incluyendo edad, niveles de glucosa, hipertensión, IMC y si son fumadores.
**Enfoque:** Se implementó un modelo `RandomForestClassifier` para aprender los patrones de riesgo. Posteriormente, se utilizó un `TreeExplainer` de SHAP para destapar la "caja negra" del modelo.

### Resultados y Explicabilidad (XAI)
Al analizar las decisiones del modelo de clasificación, SHAP nos revela los factores más determinantes a la hora de clasificar a un paciente como "Riesgo Alto" (Clase 1):

<img width="343" height="288" alt="image" src="https://github.com/user-attachments/assets/18460264-37f1-476c-93b1-a71e1a1e004c" />


* **Conclusiones:** El modelo determina que la **Edad** es el factor de riesgo más crítico con diferencia, seguido de un nivel alto de **Glucosa** media en sangre y el **IMC** (Índice de Masa Corporal). 

---

## 💸 Caso de Uso 2: Modelo de Regresión (Costes Médicos)

**Objetivo:** Predecir el coste exacto anual de la factura médica de una persona basándonos en sus características físicas y demográficas.
**Dataset:** *Medical Cost Personal Dataset* (Kaggle). Incluye edad, sexo, IMC, cantidad de hijos, región y estado de fumador.
**Enfoque:** Se entrenó un modelo `RandomForestRegressor` capaz de predecir valores continuos (dólares/euros). Se aplicó SHAP para cuantificar el impacto económico de cada variable.

### Resultados y Explicabilidad (XAI)
El análisis de impacto de SHAP nos muestra cómo cada factor empuja el precio de la factura hacia arriba o hacia abajo:

<img width="418" height="229" alt="image" src="https://github.com/user-attachments/assets/00caa0ea-49ad-48b9-a7c5-0864eb07ad08" />



* **Conclusiones:** La explicabilidad revela de forma contundente que **ser fumador** (`smoker_yes`) es la variable que más encarece los costes médicos, desplazando la predicción económica drásticamente hacia valores altos (puntos rojos a la derecha). La edad y un IMC elevado son los siguientes factores que más peso económico añaden a la predicción.

---

## 🛠️ Tecnologías Utilizadas
* **Lenguaje:** Python
* **Librerías de Modelado:** `scikit-learn` (Random Forest)
* **Librerías XAI:** `shap`
* **Manipulación de Datos:** `pandas`
