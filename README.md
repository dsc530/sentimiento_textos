# 🧠 Análisis de Sentimientos de Opiniones de Productos

Este proyecto realiza un análisis de sentimientos sobre opiniones de productos, entrenando y comparando distintos enfoques de procesamiento de texto y clasificación.

---

## 🎯 Objetivos

- **Preprocesar** las opiniones normalizando y limpiando el texto.  
- **Extraer características** mediante TF-IDF y embeddings BERT.  
- **Entrenar** modelos de clasificación para predecir la polaridad (`Positiva` / `Negativa`).  
- **Evaluar** el rendimiento de cada modelo frente a un modelo base (*dummy*).

---

## 🔍 Flujo de Trabajo

1. ### Importación y Preparación  
   - Carga de librerías y recursos de NLTK y spaCy.  
   - Lectura del CSV con las opiniones y sus etiquetas.  

2. ### Preprocesamiento de Texto  
   - Minúsculas, eliminación de puntuación y espacios extras.  
   - Lemmatización con NLTK y con spaCy.  

3. ### Extracción de Características  
   - **TF-IDF** sobre tokens de NLTK y de spaCy.  
   - **Embeddings** con un modelo BERT preentrenado.  

4. ### División de Datos  
   - Separación en entrenamiento y prueba (80 %/20 %).  

5. ### Entrenamiento de Modelos  
   - **Regresión Logística** (TF-IDF NLTK y TF-IDF spaCy)  
   - **LightGBM** (TF-IDF)  
   - **Modelo Dummy** como referencia.  

6. ### Evaluación  
   - Cálculo de **accuracy**, **F1-score** y comparación frente al modelo dummy.

---

## 📊 Conclusiones Principales

### Análisis Exploratorio de Datos  
- La cantidad de reseñas por película tiende a aumentar con el tiempo.  
- La mayoría de las películas acumula **1–3 reseñas**, aunque existen ~400 películas con **30 comentarios**.  
- La proporción de reseñas negativas y positivas está bien balanceada en entrenamiento y prueba.  
- Muchas películas tienen **1–2 reseñas negativas**, mientras que las reseñas positivas están más distribuidas.

### Comparación de Lemmatización (NLTK vs spaCy)  
- Ambos métodos arrojan métricas casi idénticas con Regresión Logística sobre TF-IDF.  
- El vectorizador TF-IDF es el mismo en todos los casos, por lo que no introduce variación.

### Rendimiento de Modelos  
- **Regresión Logística** y **LightGBM** obtuvieron F1 en entrenamiento entre **0.91–0.94** y en prueba entre **0.86–0.88**.  
- Todos superaron ampliamente al modelo **dummy**.  

### Modelos con Datos Manuales  
- Al clasificar manualmente comentarios como positivos o negativos:
  - **LightGBM** fue el mejor modelo de predicción.  
  - La **Regresión Logística con spaCy** fue el de peor resultado.  
  - Los F1 finales son muy similares a los obtenidos en conjunto de prueba (~0.88).

---

## ## 🧰 Requisitos del Entorno

- Python 3.8 o superior  
- pandas  
- numpy  
- scikit-learn  
- matplotlib  
- seaborn  
- nltk  
- spacy  
- transformers  


