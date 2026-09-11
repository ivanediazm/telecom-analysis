# ConnectaTel Customer Behavior Analysis

## Project Overview

This project analyzes customer behavior for **ConnectaTel**, a telecommunications company, with the objective of identifying usage patterns, customer segments, potential data quality issues, and opportunities to improve customer retention and plan design.

The analysis focuses on three main data sources:

* Customer information
* Mobile plan characteristics
* Usage records for calls and text messages

The project combines **data cleaning, customer segmentation, exploratory data analysis, outlier detection, and business-oriented recommendations**.

---

## Business Questions

The analysis aims to answer questions such as:

* What data quality issues exist in the customer and usage datasets?
* How can customers be segmented by age and usage level?
* Which customer groups may represent greater commercial value?
* Are there customers with unusually high usage patterns?
* How do Basic and Premium customers differ in their behavior?
* What retention or product opportunities can be identified from usage patterns?
* Could ConnectaTel improve its current plans based on customer behavior?

---

## Data Sources

The project uses three datasets:

### `plans.csv`

Contains information about ConnectaTel's available plans, including:

* Monthly price
* Included minutes
* Included messages
* Included data
* Additional usage costs

The company offers two main plans:

* **Basic**
* **Premium**

### `users_latam.csv`

Contains customer-level information such as:

* Customer ID
* Age
* City
* Registration date
* Churn date
* Current plan

### `usage.csv`

Contains customer usage records, including:

* Calls
* Text messages
* Call duration
* Message length
* Date of activity

---

## Methodology

The project followed a structured analytical workflow.

### 1. Data Exploration

The datasets were initially reviewed to understand:

* Data types
* Missing values
* Categorical variables
* Invalid values
* Dataset structure

Special attention was given to fields such as age, city, registration dates, churn dates, call duration, and message length.

---

### 2. Data Cleaning

Several data quality issues were identified and treated.

Main cleaning actions included:

* Replacing the invalid age sentinel `-999` with the median age calculated from valid observations.
* Replacing the city sentinel `"?"` with missing values.
* Converting date columns to datetime format.
* Marking dates after 2024 as invalid because they fall outside the analysis period.
* Preserving missing values in `duration` and `length` when they were explained by the type of activity.

For example, call records use `duration`, while text message records use `length`, so these missing values should not automatically be treated as data errors.

---

## Customer Segmentation

### Age Segmentation

Customers were grouped into three age categories:

* **Young:** under 30 years old
* **Adult:** between 30 and 59 years old
* **Senior:** 60 years old or older

This segmentation allows customer behavior and plan distribution to be compared across different age groups.

### Usage Segmentation

Customers were also classified according to their level of activity:

* **Low Usage:** fewer than 5 calls and fewer than 5 messages
* **Medium Usage:** customers who do not qualify as low usage and have fewer than 10 calls and fewer than 10 messages
* **High Usage:** remaining customers with higher activity levels

This classification helps distinguish between low-engagement customers and users with potentially greater commercial value.

---

## Exploratory Data Analysis

Visualizations were used to understand customer behavior and compare usage patterns between plans.

The analysis included:

* Distribution of customer age
* Number of calls by customer
* Number of messages by customer
* Call duration
* Usage patterns by plan
* Customer segmentation
* Boxplots for detecting unusual values

The project uses Python visualization libraries to explore these patterns and communicate results clearly.

---

## Outlier Analysis

Potential outliers were identified using:

* Boxplots
* Interquartile Range (IQR)

The analysis focused on:

* Age
* Number of messages
* Number of calls
* Total call minutes

Rather than automatically removing extreme observations, the project treats them as cases that should first be investigated.

In a telecommunications context, unusually high usage may represent a **valuable heavy-usage customer** rather than an incorrect record.

---

## Key Business Insights

### 1. High-usage customers represent an important commercial segment

Customers with unusually high call or messaging activity may represent a valuable segment for ConnectaTel.

Instead of treating these observations only as statistical outliers, they can be analyzed as potential high-value customers.

---

### 2. Plan selection should be evaluated against actual usage

The analysis compares customer activity with the characteristics of the Basic and Premium plans.

This creates an opportunity to identify customers whose behavior may not be aligned with their current plan.

For example, high-usage customers still enrolled in the Basic plan may be candidates for targeted migration offers.

---

### 3. Low-usage customers may require a different commercial strategy

Customers with consistently low activity may have different needs from high-usage customers.

Possible strategies could include:

* Lower-cost plans
* Engagement campaigns
* Usage incentives
* Customized benefits

---

### 4. Outliers should not automatically be removed

Extreme usage observations can contain meaningful business information.

Before excluding them, ConnectaTel should determine whether they represent:

* Data-entry errors
* Exceptional but legitimate behavior
* High-value customer profiles

---

### 5. Churn analysis can be strengthened through segmentation

Customer churn should be evaluated by:

* Age group
* Usage segment
* Current plan

This can help identify customer groups with higher abandonment risk and improve retention strategies.

---

## Recommendations

Based on the analysis, ConnectaTel could consider the following actions:

* Design retention campaigns for high-usage customers.
* Identify Basic-plan customers with heavy usage who could benefit from Premium.
* Evaluate whether a new intermediate plan between Basic and Premium is justified by customer behavior.
* Create engagement strategies for low-usage customers.
* Analyze mobile data consumption in addition to calls and messages.
* Compare customer usage with each plan's included limits.
* Analyze churn by customer segment and plan.
* Maintain extreme but plausible observations as part of the analysis rather than automatically deleting them.
* Improve data-entry validation for fields such as age, city, and registration dates.

These recommendations are consistent with the final recommendations documented in the project notebook.

---

## Tools & Technologies

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Google Colab
* Jupyter Notebook

---

## Skills Demonstrated

This project demonstrates experience in:

* Data Cleaning
* Missing Value Analysis
* Data Type Conversion
* Sentinel Value Treatment
* Customer Segmentation
* Exploratory Data Analysis
* Data Visualization
* Outlier Detection
* IQR Method
* Customer Behavior Analysis
* Churn Analysis
* Business Insight Generation
* Data-Driven Recommendations

---

## Repository Structure

```text
telecom-analysis/
├── README.md
├── telecom_analysis.ipynb
├── plans.csv
├── users_latam.csv
└── usage.csv
```

---

## How to Run the Project

The notebook can be opened and executed using **Google Colab**.

1. Open `telecom_analysis.ipynb`.
2. Upload the required CSV files.
3. Make sure the files are available in `/content/`.
4. Run the notebook cells in order.

Example:

```python
plans = pd.read_csv('/content/plans.csv')
users = pd.read_csv('/content/users_latam.csv')
usage = pd.read_csv('/content/usage.csv')
```

---

## Conclusion

This project shows how customer usage data can be transformed into actionable business insights for a telecommunications company.

By combining customer segmentation, usage analysis, outlier detection, and churn-oriented recommendations, the analysis provides a foundation for improving plan design, customer retention, and commercial targeting.

Future analysis could incorporate mobile data consumption, monthly behavior over time, and customer-level revenue to estimate customer value more accurately.
