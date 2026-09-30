# 🎒 Bag Production Trend Analysis & Capacity Planning

A comprehensive data analysis and predictive modeling project examining 144 months (12 years) of manufacturing output for a bag production facility (**EGIER**). The project utilizes a **Degree-3 Polynomial Regression** model to characterize non-linear production growth and employs the **Newton-Raphson numerical method** to forecast the optimal timeline for warehouse capacity expansion.

---

## 📌 Project Overview & Business Case

As demand grows, maintaining adequate warehousing and inventory throughput is critical for manufacturing supply chain resilience. This study investigates:
1. **Historical Production Analysis:** Evaluating monthly manufacturing volume across 144 recorded intervals ($M_1$ through $M_{144}$).
2. **Polynomial Curve Fitting:** Formulating a cubic trend equation ($\hat{y} = ax^3 + bx^2 + cx + d$) to capture acceleration in production volume.
3. **Model Evaluation:** Measuring model goodness-of-fit via Coefficient of Determination ($R^2$), Mean Squared Error (MSE), and Root Mean Squared Error (RMSE).
4. **Capacity Planning Optimization:** Computing the exact future month when production volume surpasses current facility limits (25,000 units/month) and identifying when to begin construction considering a 13-month lead time.

---

## 📈 Model Formulation & Evaluation

### 1. Polynomial Model Equation
Using least-squares polynomial approximation, the fitted 3rd-degree equation is:

$$\hat{y}(x) = 0.004x^3 - 0.134x^2 + 47.22x + 1749$$

*Where $x$ represents the month index and $\hat{y}$ is the projected monthly bag output.*

### 2. Accuracy & Fit Metrics
* **Coefficient of Determination ($R^2$):** **0.996** (explaining 99.6% of the variance in historical production)
* **Mean Squared Error (MSE):** `83,195.127`
* **Root Mean Squared Error (RMSE):** `288.436 units`

---

## 🏭 Business Insights: Warehouse Expansion Planning

* **Maximum Current Storage Capacity:** $25,000\text{ units/month}$
* **Construction Lead Time:** $13\text{ months}$
* **Newton-Raphson Numerical Root Finding:**
  * Projected production exceeds $25,000\text{ units}$ at **Month 168**.
  * Groundbreaking and facility construction must commence by **Month 155** ($168 - 13$) to avert logistical bottlenecks and inventory overflows.

---

## 🛠️️ Tech Stack & Dependencies

* **Language:** Python 3.x
* **Data Manipulation:** `pandas`, `numpy`
* **Data Visualization:** `matplotlib`
* **Numerical Methods:** `scipy` / custom implementation of `Newton-Raphson algorithm`

---

## 📁 Repository Structure

```text
├── data/
│   └── aol_data.csv          # Historical 144-month production data
├── notebooks/
│   └── aol_scicom.ipynb      # Main analysis, curve fitting, and simulation
├── README.md                 # Project documentation
```
