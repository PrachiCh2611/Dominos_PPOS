# 🍕 Domino's Pizza Sales Forecasting & Ingredient Ordering System

## 📌 Project Overview
This project is designed to help Domino's automate their ingredient ordering system by forecasting pizza sales using time series models. The final output is a **purchase order** detailing the required quantity of each ingredient for the upcoming week, based on forecasted pizza demand.

---

## 📂 Files Included
- `Pizza_Sale - pizza_sales.csv`: Historical pizza sales data.
- `Pizza_ingredients - Pizza_ingredients.csv`: Ingredient quantities required per pizza.
- `Full_Dominos_Sales_Forecasting.ipynb`: Complete Jupyter notebook with EDA, model training, forecasting, and ingredient calculations.
- `Ingredient_Purchase_Order.csv`: Auto-generated purchase order for next week.
- `*.png`: Visualizations (sales trend, forecast, ingredient bar chart).

---

## 🚀 Step-by-Step Workflow

### 1. Import Libraries
Standard libraries like `pandas`, `matplotlib`, `seaborn`, and time series model from `statsmodels`.

---

### 2. Load Datasets
```python
sales_df = pd.read_csv('Pizza_Sale - pizza_sales.csv')
ingredients_df = pd.read_csv('Pizza_ingredients - Pizza_ingredients.csv')
```
Date format is parsed using `dayfirst=True`.

---

### 3. Exploratory Data Analysis (EDA)
- Check for nulls and data types
- Sales distribution by:
  - Pizza size
  - Category
  - Weekday
  - Month
- Detect trends and seasonality

---

### 4. Data Preprocessing
- Convert `order_date` to datetime
- Drop any `NaT` values
- Aggregate pizza sales weekly for time series analysis

---

### 5. Model Selection & Forecasting
- **Model Used**: SARIMA `(1,1,1)(1,1,1,52)`
- **Reason**:
  - Handles seasonality
  - Good performance (MAPE reported)
  - Interpretable and robust for business data

```python
from statsmodels.tsa.statespace.sarimax import SARIMAX
```

- Split data into train/test
- Fit the SARIMA model
- Forecast for:
  - 4-week test period (for evaluation)
  - 1-week future (for purchase order)

---

### 6. Forecast Evaluation
- Metric used: **Mean Absolute Percentage Error (MAPE)**
- Visualizations compare actual vs forecasted weekly sales

---

### 7. Ingredient Requirement Calculation
- Forecast total number of pizzas
- Estimate breakdown by pizza type (based on historical proportions)
- Use `Pizza_ingredients` mapping to multiply pizza quantity × ingredient grams
- Group by ingredient and calculate total grams needed

---

### 8. Output
- Save final ingredient requirements to `Ingredient_Purchase_Order.csv`
- Visualize top ingredients using bar chart

---

## 📈 Visualizations
- Weekly sales trend line chart
- Forecasted vs actual sales plot
- Bar chart of total ingredient quantities

---

## 🧠 Key Insights
- SARIMA provides reliable short-term sales forecasts
- Automated ordering minimizes overstock/shortage
- Historical sales patterns show weekly and monthly seasonality

---

## ⚙️ Setup Instructions

### 1. Install Required Libraries
```bash
pip install pandas matplotlib seaborn statsmodels scikit-learn
```

### 2. Run the Notebook
Open `Dominos_Sales_Forecasting.ipynb` in Jupyter Notebook or Google Colab.

---


