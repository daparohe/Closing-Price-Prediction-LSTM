# 🧠 Desarrollo de Modelo LSTM para Predicción de Precios de Cierre en Trading Algorítmico

Este repositorio contiene los recursos y código fuente utilizados en la investigación:
"Desarrollo de Modelo LSTM para Predicción de Precios de Cierre en Trading Algorítmico"

El objetivo principal es implementar y validar un modelo de red neuronal LSTM para la predicción de precios de cierre del par EUR/USD, utilizando técnicas avanzadas de preprocesamiento, ingeniería de características y validación temporal, en el marco del trading algorítmico.

## 📁 Contenido del Repositorio
LSTM_TA.ipynb:
- Notebook principal con el desarrollo completo del modelo LSTM y modelos de comparación (ARIMA y XGBoost).

data_extraction.ipynb:
- Notebook de extracción y limpieza de datos históricos desde Yahoo Finance (vía yfinance)

todos_1d_10y.csv:
- Dataset histórico de varios símbolos (activos), incluyendo el EUR/USD (2015–2025) utilizado para el entrenamiento. Instancias diarias.

## 🧩 Estructura del Proyecto
1. Extracción de Datos:
- Descarga de datos OHLCV (Open, High, Low, Close, Volume) del EUR/USD.
- Período: 30 de noviembre de 2015 – 24 de noviembre de 2025.
2. Preprocesamiento:
- Cálculo de retornos, medias móviles (SMA 10, 30) y suavizado de volumen.
- Normalización MinMaxScaler y creación de secuencias con ventana de 60 períodos.
3. Modelado LSTM:
- Arquitectura: 2 capas LSTM (128 y 64 unidades) + Dropout 20%.
- Entrenamiento con Adam, early stopping y validación temporal.
4. Validación Walk-Forward:
- Reentrenamiento cada 30 días para simular condiciones reales.
5. Comparación con Modelos Base:
- ARIMA(0,1,0) y XGBoost con secuencias aplanadas.
6. Evaluación:
- Métricas: MSE, RMSE, MAE, R², Accuracy, MAPE.

## ⚙️ Requisitos
Para ejecutar los notebooks se recomienda un entorno con Python 3.11 y las siguientes librerías:

```pip install numpy pandas matplotlib seaborn scikit-learn yfinance tensorflow statsmodels xgboost jupyter```

## 🚀 Ejecución
Clonar el repositorio y ejecutar los notebooks en el orden sugerido:

```git clone https://github.com/daparche/Closing-Price-Prediction-LSTM.git```

```cd Closing-Price-Prediction-LSTM```

```jupyter notebook data_extraction.ipynb``` (opcional, ya se incluye el CSV)

```jupyter notebook LSTM_TA.ipynb```

## 📊 Resultados Esperados
El modelo LSTM permite estimar tendencias en precios de cierre y analizar su efectividad para estrategias de trading algorítmico, sirviendo como herramienta de apoyo en investigación y práctica financiera. Las métricas esperadas son:

✅ MSE: 0.000105

✅ R²: 0.9949

✅ Accuracy: 98.52%

✅ MAE (walk-forward): 0.0086

✅ Superioridad frente a ARIMA y XGBoost en todas las métricas

## 📌 Notas Técnicas
- División temporal: 80% entrenamiento – 20% prueba.
- Lookback window: 60 períodos.
- Dropout: 20% para evitar sobreajuste.
- Early Stopping: Paciencia de 10 épocas.
- Optimizador: Adam (lr=0.001).

## Transparencia Académica
Este repositorio se publica con el fin de garantizar la transparencia técnica y académica, permitiendo la reproducibilidad total de los experimentos presentados en el artículo.

## Autores
David Paúl Rosales Herrera

📧Correo: daparohe@gmail.com

Jhon Paúl	Villamarín Tapia

📧Correo: jhvillamarint@ists.edu.ec
