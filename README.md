# AI-IoT-Plant-Care-System
# AI-Driven IoT Plant Care System Using Knowledge Distillation for Edge Deployment

## Overview

This project presents an intelligent plant-care system that combines Artificial Intelligence (AI), Internet of Things (IoT), and Edge Computing to enable autonomous plant monitoring and decision-making.

The system analyzes environmental and soil conditions, predicts appropriate corrective actions, and deploys a lightweight machine learning model on a Raspberry Pi through Knowledge Distillation. By moving intelligence from the cloud to the edge, the system can operate with low latency and limited internet connectivity while maintaining strong predictive performance.

Developed as part of the ECE333 Introduction to Artificial Intelligence course.

---

## Project Objectives

* Develop an AI-enabled system for autonomous

plant care

* Evaluate crop suitability through real-time sensor

data

* Deploy a lightweight model on Raspberry Pi using

knowledge distillation

* Predict optimal actions and estimate expected

improvement

* Automatically control irrigation, cooling, pH,

nutrients, and heating

* Estimate suitability gain to measure improvement

after each action.


---

## Key Features

### Environmental Monitoring

The system utilizes environmental and soil-related parameters including:

* Soil Moisture
* Temperature
* Humidity
* Soil pH
* Nitrogen (N)
* Phosphorus (P)
* Potassium (K)

### AI-Based Recommendations

The model predicts plant-care actions such as:

* Increase Irrigation
* Reduce Irrigation
* Activate Cooling
* Increase Temperature
* Increase Soil pH
* Decrease Soil pH
* Add Nitrogen Fertilizer
* Add Phosphorus Fertilizer
* Add Potassium Fertilizer
* Maintain Current Conditions

### Knowledge Distillation

A cloud-trained teacher model transfers knowledge to a lightweight student model suitable for Raspberry Pi deployment.

Benefits include:

* Faster inference
* Lower memory usage
* Offline operation
* Reduced computational requirements

### Suitability Gain Prediction

A regression model estimates the expected improvement in crop suitability after applying the recommended actions, providing additional transparency and explainability.

---

## Dataset

This project uses two datasets.

### 1. Smart Farming Data 2024 (SF24)

The primary dataset is based on the Smart Farming Data 2024 (SF24) dataset obtained from Kaggle.

The repository includes a processed version:

```text
Crop_recommendationV2.csv
```

This dataset was cleaned and prepared for machine learning experiments and multi-label decision prediction.

### 2. Custom Crop Metadata Dataset

A custom crop metadata dataset was created specifically for this project:

```text
plant_metadata_detailed_numeric.csv
```

This dataset contains crop-specific agricultural knowledge including:

* Optimal temperature ranges
* Humidity ranges
* pH requirements
* Nitrogen requirements
* Phosphorus requirements
* Potassium requirements
* Rainfall requirements
* Crop characteristics

The metadata dataset is integrated with SF24 to support crop-specific suitability scoring, feature engineering, and explainable recommendations.

---

## Machine Learning Pipeline

### Data Processing

* Data cleaning
* Metadata integration
* Feature engineering
* Multi-label action generation
* Feature scaling

### Teacher Model (Cloud)

Architecture:

```text
Input
 ↓
Dense(128)
 ↓
Dense(64)
 ↓
Dense(32)
 ↓
Multi-Label Output
```

Purpose:

* Learn complex relationships between environmental conditions and plant-care actions.

### Student Model (Edge)

Architecture:

```text
Input
 ↓
Dense(64)
 ↓
Dense(32)
 ↓
Multi-Label Output
```

Purpose:

* Lightweight deployment on Raspberry Pi.

Knowledge Distillation Temperature:

```text
T = 2
```

---

## System Architecture

```text
Environmental Sensors
        │
        ▼
Feature Engineering
        │
        ▼
Teacher Model (Cloud)
        │
Knowledge Distillation
        │
        ▼
Student Model (Raspberry Pi)
        │
        ▼
Action Prediction
        │
        ▼
Actuator Control
```

---

## Hardware Components

### Controller

* Raspberry Pi 3

### Sensors

* DHT22 Temperature & Humidity Sensor
* Soil Moisture Sensor
* LM35 Temperature Sensor
* pH Sensor
* NPK Sensor
* MCP3208 ADC

### Actuators

* Water Pump
* Cooling Fan
* Relay Module

### Display

* 16×2 LCD (I2C)

---

## Results

### Teacher Model

| Metric            | Value |
| ----------------- | ----- |
| Micro F1 Score    | 0.93  |
| Weighted F1 Score | 0.93  |
| Macro F1 Score    | 0.77  |

### Student Model

| Metric          | Value  |
| --------------- | ------ |
| Binary Accuracy | 94.94% |
| Precision       | 94.18% |
| Recall          | 88.87% |
| Loss            | 0.1364 |

### Suitability Gain Model

| Metric | Value  |
| ------ | ------ |
| R²     | 0.9992 |
| MAE    | 0.1563 |
| RMSE   | 0.5073 |

---

## Technologies Used

### Programming

* Python

### Machine Learning

* TensorFlow
* Keras
* Scikit-Learn

### Data Analysis

* Pandas
* NumPy
* Matplotlib
* Seaborn

### Edge Deployment

* Raspberry Pi
* TensorFlow Lite

### IoT

* GPIO
* MCP3208 ADC
* Environmental Sensors

---

## Repository Structure

```text
data/
├── Crop_recommendationV2.csv
└── plant_metadata_detailed_numeric.csv

notebooks/
└── AI_IoT_Plant_Care_System.ipynb

docs/
├── AIproject_AlaaH_Layan_Amro_Maha.pdf
└── ai_ppt.pdf
```

---

## Future Improvements

* Mobile application integration
* Solar-powered deployment
* Additional crop support
* Remote monitoring dashboard
* Automated nutrient dosing
* Automated pH correction system

---

## Authors

* Alaa Hallak
* Layan Turkistani
* Amro Yousef
* Maha Alblwai

Effat University

---

## Academic Project

This repository is provided for educational and portfolio purposes.
