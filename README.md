# Airline Passenger Satisfaction Prediction

This project aims to predict airline passenger satisfaction using various machine learning models. I analyzed a comprehensive dataset, performed extensive data preprocessing, and conducted rigorous experimentation, including feature selection and hyperparameter tuning, to identify the most effective model and the key factors influencing passenger satisfaction. The final comparison focuses on the best-performing Random Forest and SVM models.

## 📄 Dataset

The dataset used in this project is the **Airline Passenger Satisfaction** dataset, available on Kaggle. It contains information on various flight characteristics and customer service metrics, along with a 'satisfaction' target variable.

* **Source:** [Kaggle - Airline Passenger Satisfaction](https://www.kaggle.com/datasets/teejmahal20/airline-passenger-satisfaction)
* **Total Records:** 103,904

***

## ⚙️ Data Preprocessing

Data preprocessing was a crucial step to ensure the quality and reliability of the models. The following steps were performed in sequence:

1.  **Handling Missing Values:** I identified and removed 310 null values from the initial dataset, resulting in a clean dataset of 103,594 records.
    * Initial Records: 103,904
    * Records after cleaning: 103,594

2.  **Outlier Filtering:** I filtered out records that might not provide reliable feedback. This included passengers under 18 years of age and flights with a distance of less than 400 km.
    * Dissatisfied/Neutral Passengers after filtering: 37,731
    * Satisfied Passengers after filtering: 35,602

3.  **Categorical Feature Conversion:** All categorical features (`Gender`, `Customer.Type`, `Type.of.Travel`, `Class`, `satisfaction`) were converted to factors to prepare them for modeling.

4.  **Addressing Class Imbalance:** The initial dataset had a class imbalance. To rectify this, the **ROSE (Randomly Over Sampling Examples)** technique was applied.
    * Dissatisfied/Neutral Passengers after ROSE: 37,027
    * Satisfied Passengers after ROSE: 36,306

5.  **Feature Encoding:**
    * Binary categorical features (`Gender`, `Customer.Type`, `Type.of.Travel`) were converted to numerical values (0 and 1).
    * The `Class` feature (with three categories: Business, Eco, and Eco Plus) was **One-Hot Encoded**.

***

## 🧪 Experimentation and Model Development

Extensive experimentation was conducted to find the optimal model configuration, involving hyperparameter tuning and various feature selection methods.

### Hyperparameter Tuning

Hyperparameter tuning was performed primarily for the Random Forest model using a grid search with cross-validation. Different combinations of `mtry` (number of variables randomly sampled at each split) and `ntree` (number of trees) were explored to maximize accuracy while preventing overfitting. This iterative process helped in finding a robust set of hyperparameters for the final Random Forest model.

### Feature Selection Methods

Several feature selection techniques were applied and evaluated to identify the most relevant predictors, simplify models, and potentially improve performance.

1.  **Recursive Feature Elimination (RFE):** RFE was applied to systematically remove features, building a model each time and checking the performance. This method helped identify the most impactful subset of features by iteratively eliminating the weakest ones.

2.  **Gini Impurity (Random Forest Importance):** Leveraging the Random Forest model's intrinsic ability to rank feature importance, I used the Mean Decrease Gini metric. This measure quantifies how much each feature contributes to the homogeneity of nodes in the trees. Features with higher Mean Decrease Gini were considered more important.

<img width="1394" height="862" alt="meandecreasegini" src="https://github.com/user-attachments/assets/ce67c8c5-fa4b-458f-856f-610828739776" />

* **Top 3 Most Important Features (based on Mean Decrease Impurity):**
        1.  Online boarding
        2.  Inflight wifi service
        3.  Class_Business

3.  **Information Gain:** Features were also evaluated based on their Information Gain. This method measures the reduction in entropy (or uncertainty) after splitting a dataset based on a particular feature. Features yielding higher information gain were prioritized.

4.  **Principal Component Analysis (PCA):** PCA was used as a dimensionality reduction technique to transform the original features into a new set of orthogonal components. This helped in identifying potential latent structures in the data and reducing multicollinearity, which can be beneficial for models like SVM.

### Final Model Selection

After comprehensive experimentation with different models, feature sets, and hyperparameters, the **Random Forest** and **Support Vector Machine (SVM)** models emerged as the best two performers for this prediction task. The final code reflects the optimized versions of these models.

***

## 🔍 Feature Importance Visualizations

Beyond numerical metrics, visualizations of feature importance provided valuable insights into which aspects of the airline experience most significantly influence passenger satisfaction.

<img width="1394" height="862" alt="meandecreaseaccuracy" src="https://github.com/user-attachments/assets/ecc91fea-7594-4ed8-a340-63e1411134fe" />

The Mean Decrease in Accuracy plot from the Random Forest model further highlights the most influential features, with `Inflight.wifi.service` and `Type.of.Travel` being among the most impactful. This reinforces the importance of these services and travel context in determining overall passenger satisfaction.

***

## 📊 Model Performance Comparison and Key Findings

The performance of the selected Random Forest and SVM models was rigorously compared across several key metrics: Accuracy, F1-Score, Precision, and Recall.

<p align="center">
  <img src="[https://github.com/user-attachments/assets/26cd96f8-3f26-4210-9d3d-d43f048a225e](https://github.com/user-attachments/assets/26cd96f8-3f26-4210-9d3d-d43f048a225e)" alt="Model Performance Comparison" width="600"/>
</p>

**Key Findings:**

* **Random Forest** consistently outperformed the SVM model across all metrics. It achieved an impressive **Accuracy of 96.6%**, which is significantly higher than SVM's 88.0%.
* The high **Recall (97.6%)** for the Random Forest model indicates its strong ability to correctly identify satisfied passengers, minimizing false negatives.
* The **Precision (95.8%)** for Random Forest also demonstrates its effectiveness in making accurate positive predictions.
