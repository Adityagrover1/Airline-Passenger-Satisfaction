# Airline Passenger Satisfaction Prediction

This project aims to predict airline passenger satisfaction using various machine learning models. I analyzed a comprehensive dataset, performed extensive data preprocessing, and compared the performance of a Random Forest and an SVM model to identify the key factors influencing passenger satisfaction.

## 📄 Dataset

The dataset used in this project is the **Airline Passenger Satisfaction** dataset, available on Kaggle. It contains information on various flight characteristics and customer service metrics, along with a 'satisfaction' target variable.

* **Source:** [Kaggle - Airline Passenger Satisfaction](https://www.kaggle.com/datasets/teejmahal20/airline-passenger-satisfaction)
* **Total Records:** 103,904

## ⚙️ Data Preprocessing

Data preprocessing was a crucial step to ensure the quality and reliability of the models. The following steps were performed in sequence:

1.  **Handling Missing Values:** We identified and removed 310 null values from the initial dataset, resulting in a clean dataset of 103,594 records.
    * Initial Records: 103,904
    * Records after cleaning: 103,594

2.  **Outlier Filtering:** We filtered out records that might not provide reliable feedback. This included passengers under 18 years of age and flights with a distance of less than 400 km.
    * Dissatisfied/Neutral Passengers after filtering: 37,731
    * Satisfied Passengers after filtering: 35,602

3.  **Categorical Feature Conversion:** All categorical features (`Gender`, `Customer.Type`, `Type.of.Travel`, `Class`, `satisfaction`) were converted to factors to prepare them for modeling.

4.  **Addressing Class Imbalance:** The initial dataset had a class imbalance. To rectify this, the **ROSE (Randomly Over Sampling Examples)** technique was applied.
    * Dissatisfied/Neutral Passengers after ROSE: 37,027
    * Satisfied Passengers after ROSE: 36,306

5.  **Feature Encoding:**
    * Binary categorical features (`Gender`, `Customer.Type`, `Type.of.Travel`) were converted to numerical values (0 and 1).
    * The `Class` feature (with three categories: Business, Eco, and Eco Plus) was **One-Hot Encoded**.

## 📊 Model Selection and Results

We chose two powerful machine learning models, **Random Forest (RF)** and **Support Vector Machine (SVM)**, and compared their performance. Both models were trained and validated using a 10-fold cross-validation approach.

### Random Forest
The Random Forest model was trained with 200 trees. Feature importance was also analyzed to understand the key drivers of satisfaction.

* **Top 3 Most Important Features (based on Mean Decrease Impurity):**
    1.  Online boarding
    2.  Inflight wifi service
    3.  Class_Business

### SVM
A linear SVM model was trained on the dataset to provide a baseline for comparison.

### Model Performance Comparison
The performance of both models was compared across several key metrics: Accuracy, F1-Score, Precision, and Recall. The Random Forest model consistently outperformed the SVM model across all metrics.

**Key Findings:**
* **Random Forest** achieved an **Accuracy of 96.6%**, which is significantly higher than SVM's 88.0%.
* The high **Recall (97.6%)** for the RF model indicates its effectiveness in correctly identifying satisfied passengers.

