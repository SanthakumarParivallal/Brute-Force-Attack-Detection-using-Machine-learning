# 🛡️ Brute Force Attack Detection Using Machine Learning

## 📌 Project Overview
This project focuses on detecting network intrusions, specifically brute force attacks (FTP and SSH), using various machine learning and deep learning algorithms. Since the dataset contains known input features and labels, we utilize a supervised learning classification approach to predict whether incoming network traffic is Normal (Benign) or a Brute force attack.

## 📊 Dataset Details
The data used for this project is from the CSE-CIC-IDS2018 dataset.
* **File Name:** `02-14-2018.csv`
* **Source:** Kaggle
* **Total Records:** 1,048,575 network flow records
* **Features:** 80 columns in total (79 input features + 1 target variable: `Label`)
* **Class Distribution:**
  * `Benign`: ~667k records
  * `FTP-BruteForce`: ~193k records
  * `SSH-Bruteforce`: ~187k records

## 🧠 Algorithms Evaluated
We evaluate a total of 4 traditional machine learning algorithms and 2 deep learning algorithms.

### Traditional Machine Learning
1. **Logistic Regression:** A simple baseline model that works well for binary classification.
2. **Decision Tree:** A highly interpretable tree-based model.
3. **Random Forest:** An ensemble learning method that combines multiple decision trees and handles large datasets effectively.
4. **Support Vector Machine (SVM):** Effective for high-dimensional data as it finds the optimal separating hyperplane.

### Deep Learning
5. **Artificial Neural Network (ANN):** A fully connected neural network capable of capturing complex patterns in network traffic.
6. **Deep Neural Network (DNN):** Features multiple hidden layers for superior feature learning capabilities.

## 📈 Evaluation Metrics
The models are strictly evaluated using 6 primary metrics to determine their real-world effectiveness:
* **Accuracy:** Measures overall correct predictions.
* **Precision:** Measures how many of the predicted attacks were actually attacks.
* **Recall (Detection Rate):** Measures how many actual attacks were correctly detected.
* **F1 Score:** Represents the balance between precision and recall.
* **Confusion Matrix:** Visually shows the true/false positive and negative prediction results.
* **ROC-AUC Score:** Measures the model’s ability to distinguish between classes, where a higher AUC indicates a better model.

## 🏆 Project Results
All models performed exceptionally well on the dataset. The **Decision Tree** and **Random Forest** algorithms tied for the highest accuracy at approximately 99.995%. 

Ultimately, the **Decision Tree** was selected as the best overall model. The trained model and its corresponding data scaler have been successfully saved (`bruteforce_attack_detection_model.pkl` and `feature_scaler.pkl`) for future deployment and predictions.
