# Customer-Shopping-Behavior-Analysis

# 🛍️ Customer Shopping Behavior Analysis using Python & Pandas, Matplotlib and Seaborn.

## 📌 Project Overview

This project focuses on analyzing customer shopping behavior using Python and Pandas. The objective was to understand customer purchasing patterns, demographics, shopping frequency, product preferences, subscription behavior, payment methods, and discount usage.

The project involved data cleaning, preprocessing, feature engineering, exploratory data analysis (EDA), and data visualization to generate meaningful business insights from customer transaction data.

---

# 🎯 Business Objective

The main objective of this project is to answer key business questions such as:

- Who are the most active customers?
- Which age groups purchase more products?
- What are the most preferred product categories?
- How frequently do customers shop?
- How do discounts influence purchasing behavior?
- Which payment methods are most popular?
- What are the customer demographics?

The analysis helps businesses understand customer behavior and improve marketing, sales, and retention strategies.

---

# 📊 Dataset Information

The dataset contains approximately **3900 customer records** with the following attributes:

| Column Name | Description |
|------------|-------------|
| Customer ID | Unique Customer Identifier |
| Age | Customer Age |
| Gender | Customer Gender |
| Item Purchased | Purchased Product |
| Category | Product Category |
| Purchase Amount (USD) | Purchase Value |
| Location | Customer Location |
| Size | Product Size |
| Color | Product Color |
| Season | Purchase Season |
| Review Rating | Customer Rating |
| Subscription Status | Subscription Information |
| Shipping Type | Shipping Method |
| Discount Applied | Discount Status |
| Promo Code Used | Promo Code Usage |
| Previous Purchases | Historical Purchases |
| Payment Method | Payment Method Used |
| Frequency of Purchases | Shopping Frequency |

---

# 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Google Colab / Jupyter Notebook

---

# 🔄 Project Workflow

## 1. Data Loading

Imported required libraries:

```python
import pandas as pd
import numpy as np
```

Loaded dataset using:

```python
data = pd.read_csv("customer_shopping_behavior.csv")
```

Checked first records:

```python
data.head()
```

Purpose:
- Understand dataset structure
- Verify successful loading

---

## 2. Data Understanding

Performed dataset exploration using:

```python
data.describe(include='all')
```

Analyzed:

- Total records
- Mean
- Median
- Maximum values
- Minimum values
- Unique values
- Most frequent values

Key Findings:

- Total Records: 3900
- Age Range: 18–70 Years
- Purchase Amount Range: 20–100 USD
- Average Review Rating: Approximately 3.75

---

## 3. Missing Value Analysis

Checked missing values:

```python
data.isnull().sum()
```

Finding:

- Review Rating contained missing values.

---

## 4. Missing Value Treatment

Filled missing ratings using category-wise median:

```python
data['Review Rating'] = data.groupby('Category')['Review Rating'] \
.transform(lambda x: x.fillna(x.median()))
```

Why?

- Median is less affected by outliers.
- Maintains data consistency.

Result:

- All missing values successfully handled.

---

## 5. Column Standardization

Converted column names into a cleaner format:

```python
data.columns = data.columns.str.lower()
data.columns = data.columns.str.replace(" ","_")
```

Example:

Before:

```text
Purchase Amount (USD)
```

After:

```text
purchase_amount_(usd)
```

Benefits:

- Easy coding
- Improved readability
- Professional dataset structure

---

## 6. Column Renaming

Renamed long column names:

```python
data.rename(columns={
'purchase_amount_(usd)':'purchase_amount'
})
```

Purpose:

- Cleaner code
- Better readability

---

## 7. Feature Engineering

### Purchase Frequency Conversion

Original values:

- Weekly
- Monthly
- Quarterly
- Annually
- Fortnightly

Converted into numerical days:

```python
Frequency_mapping = {
'Weekly':7,
'Fortnightly':14,
'Monthly':30,
'Quarterly':90,
'Annually':365
}
```

Created new column:

```python
data['purchase_frequency_days']
```

Benefits:

- Better analysis
- Suitable for machine learning
- Easier numerical comparison

---

### Customer Age Segmentation

Created customer age groups using:

```python
pd.qcut()
```

Generated Age Groups:

- Young Adult
- Adult
- Middle-aged
- Senior

Example:

```python
data['Age_group']
```

Benefits:

- Customer segmentation
- Targeted marketing
- Behavioral analysis

---

## 8. Duplicate Information Detection

Compared:

- Discount Applied
- Promo Code Used

Finding:

Both columns contained identical information.

Validation:

```python
data['Discount Applied'] == data['Promo Code Used']
```

Result:

All values matched.

Therefore redundant information was removed.

Benefits:

- Reduced dataset redundancy
- Improved data quality

---

# 📊 Exploratory Data Analysis (EDA)

## Customer Age Distribution

Visualization Tool:

Matplotlib

```python
plt.hist(data['Age'])
```

Purpose:

Understand age distribution of customers.

Insight:

Customers are distributed across all age groups from 18 to 70 years.

---

## Gender Distribution

Visualization Tool:

Seaborn

```python
sns.countplot(x='Gender', data=data)
```

Purpose:

Compare male and female customers.

Insight:

Male customers are significantly higher than female customers.

---

## Product Color Distribution

Visualization Tool:

Seaborn

```python
sns.countplot(x='Color', data=data)
```

Purpose:

Analyze customer color preferences.

Insight:

Certain colors are purchased more frequently than others.

---

# 📈 Key Business Insights

### Customer Insights

✅ Majority of customers are Male.

✅ Adult and Middle-aged customers represent a large customer segment.

✅ Customer ratings are generally positive.

---

### Shopping Behavior Insights

✅ Customers purchase products with different frequencies ranging from weekly to annually.

✅ Repeat purchases indicate customer loyalty.

✅ Subscription customers show active purchasing behavior.

---

### Product Insights

✅ Some products and categories are purchased more frequently.

✅ Product color preferences can support inventory planning.

---

### Marketing Insights

✅ Discounts and promo codes behave similarly.

✅ Customer segmentation can improve targeted marketing campaigns.

---

# 💼 Business Benefits

This analysis helps businesses:

- Understand customer behavior
- Improve customer segmentation
- Create targeted marketing campaigns
- Increase customer retention
- Optimize inventory planning
- Improve product recommendations
- Enhance customer satisfaction
- Support data-driven decision making

---

# 🚀 Future Improvements

Possible future enhancements include:

- Customer Churn Prediction
- Customer Lifetime Value Analysis
- RFM Analysis
- Recommendation System
- Customer Segmentation using Machine Learning
- Predictive Purchase Modeling
- Interactive Dashboard Development

---

# 📌 Conclusion

The Customer Shopping Behavior Analysis project demonstrates a complete data analysis workflow using Python and Pandas. The project involved data cleaning, preprocessing, feature engineering, exploratory data analysis, and visualization techniques to uncover meaningful customer behavior insights.

The analysis provides valuable information about customer demographics, shopping patterns, purchase frequency, product preferences, and marketing opportunities, enabling businesses to make informed decisions and improve overall performance.

---

# 👨‍💻 Author

**Lakhan Yadav**

Aspiring Data Analyst

### Skills

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- SQL
- Power BI
- Excel
- Data Analysis




