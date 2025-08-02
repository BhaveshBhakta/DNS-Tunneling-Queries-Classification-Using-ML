## DNS Tunneling Queries Classification

### Project Overview

This project aims to classify **DNS queries as either benign or malicious (DNS tunneling)**. By analyzing the structural characteristics of DNS queries, specifically their entropy, the goal is to develop a machine learning model that can detect and prevent a common cyberattack method used to exfiltrate data from a network.

-----

### Technical Highlights

  * **Dataset**: [Kaggle - DNS Tunneling Queries Classification](https://www.kaggle.com/datasets/saurabhshahane/dns-tunneling-queries-classification)
  * **Size**: 14999 entries, 2 columns (after loading)
  * **Key Features**:
      * A string representing the DNS query (`q+Z8AnwaBA.hidemyself.org.`) and a label. The project extracts a single numerical feature: **Entropy**.
  * **Approach**:
      * Data Cleaning: The dataset contains a header-less CSV, which was loaded and had its columns renamed. Duplicate rows were dropped.
      * Feature Engineering: The core of the preprocessing involves a custom Python function to calculate the **Shannon entropy** of each DNS query string. This single feature, `Entropy`, is used as the input for the models.
      * Exploratory Data Analysis: Checked data shape, size, info, descriptive statistics, and unique values for the target.
      * Binary Classification: The target variable 'label' indicates malicious (`1`) or benign (`0`). The dataset is imbalanced (11999 malicious vs 3000 benign), but SMOTE was not applied in the provided notebook.
      * Models Used:
          * Logistic Regression, Ridge Classifier, SVC, Random Forest, XGBoost, AdaBoost, Gradient Boosting, Bagging, Decision Tree.
  * **Best Accuracy**:
      * 99.6% with Random Forest Classifier, Bagging Classifier, and Decision Tree Classifier.
      * 99.4% with Gradient Boosting Classifier.
      * 98.9% with XGBoost Classifier.
      * The high accuracies achieved using only a single engineered feature (entropy) suggest that this metric is a very strong indicator of DNS tunneling activity.

-----

### Purpose and Applications

  * **Detect DNS tunneling attacks** in real-time, which are often used for data exfiltration and command-and-control communication.
  * Enhance network security by providing an automated system for flagging suspicious DNS queries.
  * Support cybersecurity analysts in investigating potential threats.
  * Demonstrate a highly effective, low-resource method for anomaly detection in network traffic.

-----

### Installation

Clone the repository:

```bash
git clone https://github.com/BhaveshBhakta/DNS-Tunneling-Queries-Classification-Using-ML.git
cd DNS-Tunneling-Queries-Classification-Using-ML
```

Install the necessary libraries:

```bash
pip install pandas numpy seaborn matplotlib scikit-learn xgboost
```

-----

### Collaboration

We welcome contributions to improve the project. You can help by:

  * Exploring additional features derived from the DNS query string, such as query length, number of subdomains, and character frequency distribution.
  * Comparing the effectiveness of a single-feature model with a multi-feature model.
  * Investigating alternative methods for handling the class imbalance.
  * Performing comprehensive hyperparameter tuning and cross-validation for all models.
  * Adding explainability (e.g., SHAP or LIME) to further validate the role of entropy in the model's predictions.
