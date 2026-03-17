# Brute Force Attack Detection Using Machine Learning

<img width="1600" height="500" alt="banner" src="https://github.com/user-attachments/assets/cb9a386f-7772-4e94-bf64-16bc673fb1f4" />

<p align="center">

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-orange)
![Cybersecurity](https://img.shields.io/badge/Domain-Cybersecurity-red)
![Dataset](https://img.shields.io/badge/Dataset-CSE--CIC--IDS2018-green)
![Status](https://img.shields.io/badge/Status-Completed-success)
![Task](https://img.shields.io/badge/Task-Multi--Class%20Classification-purple)

</p>

A professional cybersecurity machine learning project that detects brute force activity in network traffic using the **CSE-CIC-IDS2018** dataset. The system compares four machine learning models and two neural network models to classify traffic as **Benign**, **FTP-BruteForce**, or **SSH-Bruteforce**.

## Table of Contents

- [Project Overview](#project-overview)
- [Why This Project Matters](#why-this-project-matters)
- [Dataset Summary](#dataset-summary)
- [Project Workflow](#project-workflow)
- [Algorithms Used](#algorithms-used)
- [Tech Stack](#tech-stack)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Model Performance](#model-performance)
- [Saved Artifacts](#saved-artifacts)
- [Installation](#installation)
- [How to Run](#how-to-run)
- [Results and Insights](#results-and-insights)
- [Future Improvements](#future-improvements)
- [Author](#author)

## Project Overview

Brute force attacks are a common way attackers try to break into systems by repeatedly testing credentials. In this project, network flow records are analyzed to automatically detect malicious login attempts against FTP and SSH services.

This repository implements a complete end-to-end pipeline:

- load and inspect the dataset
- clean missing and infinite values
- encode labels
- scale features
- train multiple ML and DL models
- evaluate performance
- save the best model for deployment use

## Why This Project Matters

In real environments, security analysts need detection systems that are:

- accurate enough to catch attacks
- fast enough for operational use
- interpretable enough to explain alerts
- stable enough to deploy on large traffic volumes

This project shows that classic tree-based models can perform extremely well on structured intrusion detection data without the heavier cost of deeper neural architectures.

## Dataset Summary

**Dataset:** CSE-CIC-IDS2018  
**File used:** `02-14-2018.csv`  
**Total records:** 1,048,575  
**Total columns:** 80  
**Input features:** 79  
**Target column:** `Label`

### Target classes

| Class | Approx. Count |
|---|---:|
| Benign | 667,626 |
| FTP-BruteForce | 193,360 |
| SSH-Bruteforce | 187,589 |

### Example fields in the dataset

- `Dst Port`
- `Protocol`
- `Flow Duration`
- `Tot Fwd Pkts`
- `Tot Bwd Pkts`
- `Flow Byts/s`
- `Pkt Len Mean`
- `SYN Flag Cnt`
- `Idle Mean`

These features capture network flow behaviour and help models learn the difference between normal traffic and automated brute force activity.

## Project Workflow

<img width="1536" height="1024" alt="workflow" src="https://github.com/user-attachments/assets/27388556-4a00-483c-bfff-83b700cfcffa" />


## Algorithms Used

### Machine Learning

| Model | Purpose |
|---|---|
| Logistic Regression | Strong linear baseline for classification |
| Decision Tree | Interpretable rule-based model |
| Random Forest | Ensemble model for robust performance |
| Support Vector Machine | Powerful classifier for complex boundaries |

### Neural Network Models

| Model | Purpose |
|---|---|
| ANN | Single hidden-layer neural network |
| DNN / MLP | Deeper feedforward neural architecture |

## Tech Stack

- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **Scikit-learn**
- **Joblib**

## Exploratory Data Analysis

The pipeline includes core EDA steps before training:

- dataset shape and column inspection
- class distribution analysis
- missing value handling
- replacement of infinite values
- correlation analysis on top numeric features
- confusion matrix visualization after prediction

### Data preprocessing used

1. Remove the `Timestamp` column  
2. Replace `inf` and `-inf` values with `NaN`  
3. Drop missing rows  
4. Encode the `Label` column using `LabelEncoder`  
5. Apply `StandardScaler` to the feature matrix  
6. Split the data into train and test sets with an 80/20 ratio  

## Model Performance

The following results come from the trained models in the provided project output.

<img width="2200" height="1276" alt="model_accuracy_chart" src="https://github.com/user-attachments/assets/77d9911b-3fda-4754-adc9-3e84b7614164" />


| Model | Accuracy | Precision | Recall | F1 Score |
|---|---:|---:|---:|---:|
| Logistic Regression | 0.999588 | 0.999589 | 0.999588 | 0.999589 |
| Decision Tree | **0.999952** | **0.999952** | **0.999952** | **0.999952** |
| Random Forest | **0.999952** | **0.999952** | **0.999952** | **0.999952** |
| SVM | 0.999933 | 0.999933 | 0.999933 | 0.999933 |
| ANN | 0.999947 | 0.999947 | 0.999947 | 0.999947 |
| DNN | 0.999943 | 0.999943 | 0.999943 | 0.999943 |

### Best model

**Decision Tree** was selected as the best model in the current pipeline.

Why it stands out:

- top accuracy
- excellent precision and recall
- fast inference
- easy interpretability
- practical for real-world SOC-style workflows

## Saved Artifacts

The training pipeline saves:

- `bruteforce_attack_detection_model.pkl`
- `feature_scaler.pkl`

These files make it easier to reuse the trained model in another script, notebook, dashboard, or API.


## Installation

Clone the repository:

```bash
git clone https://github.com/yourusername/Brute-Force-Attack-Detection-Using-Machine-Learning.git
cd Brute-Force-Attack-Detection-Using-Machine-Learning
```

```Install dependencies

pip install pandas numpy matplotlib seaborn scikit-learn joblib
```


## How to Run

Place the dataset file in your working directory or inside a dataset folder, then run:

```bash
python brute_force_attack_detection.py
```

The script will:

- load the dataset
- preprocess the features
- train all models
- evaluate each model
- print comparison results
- save the selected best model

## Results and Insights

Key takeaways from this project:

- Tree-based methods performed exceptionally well on this tabular intrusion detection dataset.
- Decision Tree and Random Forest reached the highest accuracy in the current implementation.
- Neural network models also performed strongly, but they did not outperform the best tree-based models here.
- For this task, simpler models can be more operationally useful than deeper networks.

## Future Improvements

This project can be extended by adding:

- hyperparameter tuning with `GridSearchCV` or `RandomizedSearchCV`
- ROC-AUC comparison for all models
- feature importance plots for tree-based methods
- class-wise confusion matrix exports
- REST API deployment using Flask or FastAPI
- real-time network monitoring integration
- Docker support for portable deployment
- experiment tracking with MLflow or Weights & Biases

## Author

**Santhakumar Parivallal**

---

If this project helped you, give the repository a star and use it as part of your cybersecurity and machine learning portfolio.
