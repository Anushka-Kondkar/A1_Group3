Title:

Credit Card Fraud Detection Using KNN with Merchant Risk Clustering

Objective:

To detect fraudulent credit card transactions using a combination of **K-Nearest Neighbors (KNN)** and **merchant-level risk profiling** through **K-Means clustering**, supported by feature engineering and class balancing.


2. Dataset Details

We used the publicly available Fraud Detection Dataset containing:

* Transaction amount
* Transaction timestamp
* Merchant name and location
* Customer details (masked)
* Fraud label (is_fraud: 0/1)

Class imbalance:
Fraud cases form **<0.2%** of all transactions → requires SMOTE.

3. Algorithm / Model Used

a. Preprocessing Techniques

* Label Encoding for merchants
* Feature Extraction

  * Transaction hour
  * Day of week
* Dropping `unix_time` to prevent data leakage
* Scaling using **StandardScaler**

b. Merchant-Level Clustering

* Computed merchant-level statistics:

  * Avg transaction amount
  * Fraud rate
  * Latitude/Longitude

* Applied KMeans (k=3) to classify merchants as:

  * Low risk
  * Medium risk
  * High risk

c. Handling Class Imbalance

* Applied SMOTE only on training data

d. Model

* KNN Classifier (k=7, distance-weighted)

4. Results (Accuracy, Graphs, etc.)


Validation Accuracy:

≈ 98%
Metrics:

* Precision, Recall, F1-score
* Confusion Matrix
* Fraud probability output
* Merchant cluster classification

UI Result:

A Gradio-based interactive interface that predicts:

* Fraud / Legit
* Merchant risk category
* Fraud probability (%)

5. Conclusion

The combination of **merchant risk clustering** and **KNN** significantly improved fraud detection accuracy compared to using raw features.
Feature engineering (hour, day, merchant stats) strengthened model performance.
SMOTE balanced the dataset effectively, enabling KNN to classify minority fraud cases better.

6. Future Scope

* Deploy as a real-time fraud monitoring service
* Replace KNN with an ensemble: XGBoost / Random Forest
* Add geolocation anomaly detection
* Incorporate user behavioral patterns
* Build a dashboard for analysts
* Implement incremental learning for live transaction streams


7. References

1. Fraud Detection Dataset (Kaggle / original source)
2. Scikit-learn documentation
3. Imbalanced-learn documentation
4. Gradio UI documentation
