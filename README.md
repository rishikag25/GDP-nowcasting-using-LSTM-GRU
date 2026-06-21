# Macroeconomic GDP Nowcasting Framework

An end-to-end data pipeline and sequential deep learning framework designed to nowcast quarterly real GDP growth using high-frequency, multi-sector macroeconomic indicators. This framework circumvents structural publication lags by synthesizing classical econometrics with advanced deep learning architectures.


##  Pipeline Architecture

* **Data Ingestion:** Automated ingestion of 246 high-frequency multi-sector macroeconomic indicators from the FRED database.
* **Stationarity Transformation:** Execution of log-differencing and percentage change calculations across varying structural metrics.
* **Statistical Validation:** Verification of distribution stability across all time series via the Augmented Dickey-Fuller (ADF) test.
* **Dimensionality Reduction:** Extraction of localized sector volatility using an 8-sector Block-PCA model without temporal data leakage.
* **Sequential Modeling:** Sequence engineering ($T=8$) fed into Gated Recurrent Unit (GRU) and Long Short-Term Memory (LSTM) neural networks.
* **Explainable AI Integration:** Implementation of game-theoretic SHAP frameworks to calculate and map local feature attribution.
* **Nowcast Output:** Synthesis of deep learning sequences to generate real-time, predictive estimations of current-quarter GDP growth.


##  Project Overview

Traditional macroeconomic indicators like Real GDP are typically released with significant quarterly publication lags, delaying critical monetary and fiscal decision-making. This project builds a high-frequency **Nowcasting** framework that ingests real-time, multi-sector economic indicators to generate immediate, accurate estimations of current-quarter economic growth before official figures are published.


##  Data & Feature Engineering

### 1. Dataset Description
* **Data Source:** Sourced directly from the Federal Reserve Economic Data (FRED) macro database.
* **Data Dimensions:** Aggregated **246 highly granular financial and economic indicators** across **271 historical rows**, establishing a dense time-series matrix.
* **Sectors Covered:** Spans 8 critical economic domains including industrial production, labor market metrics, consumer spending, housing starts, and monetary aggregates.

### 2. Preprocessing & Stationarity Pipeline
* **Mathematical Transformations:** Applied automated **log-differencing** and percentage change transformations across structural variations to eliminate non-stationarity trends.
* **Rigorous Statistical Validation:** Subjected every processed time series to the **Augmented Dickey-Fuller (ADF) test** to guarantee strict distribution stationarity, eliminating the risk of spurious regressions.

### 3. Dimensionality Reduction
* **Block-PCA Framework:** Designed a specialized 8-sector Block-Principal Component Analysis model to condense localized volatility within individual economic domains.
* **Data-Leakage Prevention:** Implemented strict temporal train-test splitting and covariance mapping, ensuring cross-sectional dimension reduction occurred without introducing forward-looking data leakage.


##  Methodology & Modeling Approach

### 1. Sequential Deep Learning
* **Architectures Evaluated:** Trained and optimized Gated Recurrent Unit (**GRU**) and Long Short-Term Memory (**LSTM**) networks to capture long-term temporal dependencies and non-linear economic shifts.
* **Sequence Engineering:** Structured the model inputs into uniform historical sequences ($T=8$) to capture lagging economic momentum across consecutive quarters.

### 2. Explainable AI Implementation
* **SHAP Integration:** Integrated **SHapley Additive exPlanations (SHAP)** frameworks to calculate game-theoretic feature attribution.
* **Driver Mapping:** Mapped and visualized exactly how underlying sector components and historical sequences drove the neural network's final GDP nowcast outputs.


##  Tech Stack & Tooling

* **Core Programming Language:** Python
* **Data Engineering & Matrix Math:** NumPy, Pandas, Scikit-learn
* **Deep Learning Framework:** TensorFlow / Keras
* **Econometrics & Explainability:** Statsmodels (ADF Module), SHAP Library
* **Visualization Engine:** Matplotlib, Seaborn


##  Data Source & Macroeconomic Indicators

The underlying data engine ingests high-frequency macroeconomic series mapped against official quarterly targets to execute real-time tracking:

### 1. Target Variable (Quarterly)
* **Real Gross Domestic Product (GDPC1):** Inflation-adjusted, seasonally adjusted annual rate tracking total US economic output, used as the ground-truth target for model training and nowcasting validation.

### 2. High-Frequency Economic Indicators (Sourced via FRED API)
* **Production & Manufacturing:** Tracking industrial output and manufacturing sector capacity to gauge aggregate supply shocks.
* **Labor Market Metrics:** Monitoring civilian unemployment levels and weekly jobless claims to measure shifts in consumer earning power.
* **Consumer Demand & Housing:** Analyzing retail sales performance and new housing construction starts to track consumer spending momentum.
* **Monetary Policy & Financial Markets:** Utilizing the central bank's benchmark interest rate, money supply growth, and treasury yield spreads to capture shifting credit conditions.



##  Key Results & Deliverables

* **Stationarity Assurance:** Successfully transformed 100% of non-stationary macro series to clear strict ADF test critical values.
* **Feature Attribution Maps:** Generated local SHAP waterfall plots detailing the explicit economic catalysts (e.g., shifts in manufacturing vs. employment metrics) responsible for the final quarterly nowcast deviations.
