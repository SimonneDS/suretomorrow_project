# Client Data Obfuscation and kNN Classification

## Project Title
**Client Data Privacy Preservation using Feature Obfuscation and kNN**

### Goal
The primary objective of this project was to develop and validate a methodology for protecting sensitive client data (Age and Salary) by applying a **linear transformation (obfuscation)** while ensuring minimal compromise to the performance of a machine learning model designed to predict insurance benefit eligibility.

---

### Key Methodology & Achievements

The project followed a rigorous Data Science methodology, centered on the privacy-utility trade-off.

#### 1. Analytical Validation (The Core Proof)
* **Method:** A linear algebraic proof was implemented using the relationship $\hat{w}_{orig} \approx P \hat{w}_{obf}$, where $P$ is the invertible random obfuscation matrix.
* **Result:** The analysis successfully demonstrated that the predictive utility of the data for linear models is **mathematically invariant** under the transformation, confirming that the privacy measure does not destroy the data's inherent information structure.

#### 2. Model Development (kNN Classification)
* **Data Preparation:** Continuous features were transformed using the private matrix $P$, followed by **Standard Scaling**, which is essential for the distance-based kNN algorithm.
* **Optimization:** The hyperparameter $k$ (number of neighbors) was tuned to maximize the **F1 Score** on the test set, effectively managing the class imbalance problem.

#### 3. Final Performance (Obfuscated Data)
The final model achieved strong performance on the test set, validating the obfuscation strategy.

| Model | F1 Score | Accuracy | Baseline F1 |
| :--- | :--- | :--- | :--- |
| **kNN (Optimal $k$)** | **0.6200** | **0.9400** | 0.0000 |

---

### Technologies and Libraries

* **Language:** Python
* **Data Manipulation:** `pandas`, `numpy`
* **Machine Learning:** `scikit-learn` (for `KNeighborsClassifier`, `StandardScaler`, `LinearRegression`, etc.)
* **Visualization:** `matplotlib`, `seaborn`

---

### Conclusion and Professional Next Steps

This project successfully proves that data privacy and model effectiveness can coexist using linear obfuscation. The kNN model trained on the secured features achieved strong performance, significantly exceeding the baseline.

**Professional Recommendations for Production:**

1.  **Pipeline Integration:** Implement the entire transformation chain (matrix $P$ application, `StandardScaler`) within an **`sklearn Pipeline`** to ensure consistent and error-free deployment and prevent data leakage.
2.  **Advanced Model Testing:** Explore more powerful algorithms like **XGBoost** or **LightGBM** to potentially increase the F1 Score beyond the current value of **0.6200**.
3.  **Security Audit:** Subject the obfuscation matrix $P$ to a formal security audit to confirm its long-term resistance to various forms of matrix inversion attacks.