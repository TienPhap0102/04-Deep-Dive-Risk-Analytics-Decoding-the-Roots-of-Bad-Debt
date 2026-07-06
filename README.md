# **Deep-Dive Risk Analytics: Decoding the Roots of Bad Debt**

[View the live Dashboard](https://app.powerbi.com/view?r=eyJrIjoiZDY5OWY1ZjEtODYzMy00ZGMyLTg3NTEtOTQ1YWI3NDkzYzgwIiwidCI6IjM3MGZiM2I4LTMzMDYtNDg5MC05MDYzLWNjMDhiZTc4ODI1NyIsImMiOjEwfQ%3D%3D)

---

## 📖 Project Overview

In the financial lending industry, credit risk management plays a critical role in maintaining portfolio quality, reducing bad debt, and improving underwriting decisions.

This project involves the end-to-end development of a **Credit Risk Analytics Dashboard** combined with a **Machine Learning Default Prediction Workflow**. The main objective is to transform borrower and loan data into actionable insights that help identify high-risk customers, understand default drivers, and support data-driven risk management.

The system empowers risk managers to monitor loan portfolio performance, evaluate borrower risk profiles, detect early warning signals, and predict potential default cases using classification models.

---

## 🎯 Business Objectives

- **Portfolio Risk Monitoring:** Analyze the overall loan portfolio, default ratio, total loan amount, and defaulted loans.
- **Borrower Risk Profiling:** Identify high-risk borrower groups based on demographics, income, employment type, housing ownership, and credit history.
- **Loan Risk Analysis:** Evaluate how loan intention, loan grade, interest rate, and loan term influence default risk.
- **Financial Warning Detection:** Monitor early warning indicators such as DTI, LTI, credit utilization, and delinquencies.
- **Default Prediction:** Build and compare machine learning models to classify default and non-default clients.

---

## 🛠️ Tech Stack

- **Data Visualization & BI:** Power BI
- **Data Transformation:** Power Query, DAX
- **Machine Learning:** Orange Data Mining
- **Model Evaluation:** Confusion Matrix, ROC Analysis, Test & Score
- **Data Storage:** CSV, Excel
- **Documentation:** GitHub README

---

## 💾 Dataset Information

The dataset contains borrower-level credit information, loan application details, financial indicators, and demographic attributes used to analyze and predict credit default risk.

Each record represents a loan applicant with information related to income, employment, loan characteristics, credit history, debt burden, and default status.

### The target variable of this project is **loan_status**, where:

- `0` = Non-default
- `1` = Default

Below is the data dictionary defining the core fields utilized in this analysis:

| Feature | Description |
|---|---|
| `client_ID` | Unique identifier for each client. |
| `person_age` | Age of the applicant in years. |
| `person_income` | Annual income of the applicant in USD. |
| `person_home_ownership` | Home ownership status, such as `RENT`, `OWN`, or `MORTGAGE`. |
| `person_emp_length` | Employment length of the applicant in years. |
| `loan_intent` | Purpose of the loan, such as `PERSONAL`, `MEDICAL`, `EDUCATION`, and other categories. |
| `loan_grade` | Credit grade assigned to the loan, ranging from `A` to `G`. |
| `loan_amnt` | Requested loan amount in USD. |
| `loan_int_rate` | Loan interest rate in percentage. |
| `loan_status` | Loan repayment status, where `0` indicates non-default and `1` indicates default. |
| `loan_percent_income` | Percentage of applicant income allocated to loan repayment. |
| `cb_person_default_on_file` | Indicates whether the applicant has defaulted previously, with values `Y` or `N`. |
| `cb_person_cred_hist_length` | Length of the applicant's credit history in years. |
| `gender` | Gender of the applicant, such as `Male` or `Female`. |
| `marital_status` | Marital status of the applicant, such as `Single`, `Married`, `Divorced`, or `Widowed`. |
| `education_level` | Education level of the applicant, such as `High School`, `Bachelor`, `Master`, or `PhD`. |
| `country` | Country of residence of the applicant. |
| `state` | State or province of residence of the applicant. |
| `city` | City of residence of the applicant. |
| `city_latitude` | Latitude coordinate of the applicant's city. |
| `city_longitude` | Longitude coordinate of the applicant's city. |
| `employment_type` | Employment type, such as `Full-time`, `Part-time`, `Self-employed`, or `Unemployed`. |
| `loan_term_months` | Loan term in months, such as `12`, `24`, `36`, or `60`. |
| `loan_to_income_ratio` | Loan amount divided by applicant income. |
| `other_debt` | Simulated additional debt held by the applicant in USD. |
| `debt_to_income_ratio` | Total debt obligations divided by applicant income. |
| `open_accounts` | Number of open credit accounts held by the applicant. |
| `credit_utilization_ratio` | Credit utilization ratio, ranging from `0` to `1`. |
| `past_delinquencies` | Number of past delinquencies or late payments. |

### Dataset Usage

This dataset is used for two main purposes:

1. **Credit Risk Dashboarding**  
   To analyze default patterns across borrower profiles, loan characteristics, credit history, and financial health indicators.

2. **Default Prediction Modeling**  
   To train and evaluate machine learning models that classify clients into default and non-default groups.

## 🧹 Data Processing

The dataset was cleaned and prepared before building the Power BI dashboard and machine learning models.

### Missing Value Handling

| Column | Issue | Treatment |
|---|---|---|
| `person_emp_length` | Missing employment length values | Filled with the median employment length |
| `loan_int_rate` | Missing loan interest rate values | Filled with the median interest rate by `loan_grade` |

Median imputation was used because both variables are numerical and may contain outliers. For `loan_int_rate`, the median was calculated by `loan_grade` because loan grade is strongly related to interest rate and credit risk.

### Processing Steps

- Checked and removed duplicated records.
- Handled missing values in `person_emp_length` and `loan_int_rate`.
- Standardized categorical variables such as `loan_intent`, `loan_grade`, `employment_type`, and `person_home_ownership`.
- Validated numerical fields including income, loan amount, interest rate, DTI, LTI, and credit utilization.
- Created derived features such as `loan_to_income_ratio`, `debt_to_income_ratio`, `DTI_group`, `LTI_group`, and `risk_combo_segment`.
- Prepared the final cleaned dataset for Power BI dashboarding and Orange machine learning modeling.

## 🤖 Predictive Modeling Workflow

To predict the probability of default for future applications, a machine learning pipeline was constructed using Orange tool

* **Data Splitting:** The dataset was sampled and split into a 70% training set and a 30% testing set. Stratified sampling was utilized to ensure balanced class representation.
  
* **Algorithms:** Three primary classification algorithms were trained: 
  * Logistic Regression
  * Support Vector Machine (SVM)
  * Random Forest
    
* **Model Evaluation:** The models were evaluated using the Test and Score widget, Confusion Matrix, and ROC Analysis to determine the most effective predictive algorithm.

* **Outputs:** Final predictions were generated and exported to external data tables for further review.

<img width="1926" height="1486" alt="image" src="https://github.com/user-attachments/assets/e04f95a5-baec-4ef4-baa0-e8df1853f37d" />


---

## 📊 Dashboard Architecture & Key Features

The Power BI dashboard is structured into **5 interactive pages**:

### Information

The Information page introduces the project background, objectives, insight summary, and business recommendations.

- **Purpose:** Provides a high-level explanation of the credit risk analysis project.
- **Key Analysis:**
  - Defines project objectives.
  - Summarizes major risk insights.
  - Provides strategic recommendations for risk control.

<img width="1545" height="877" alt="image" src="https://github.com/user-attachments/assets/3ea206e7-8d60-44c4-9532-3f183fc5ff89" />

---

### 📈 Business Overview

  * **Purpose**: Provides a high-level executive summary of portfolio size, client volume, and overarching default trends.
  * **Key Analysis**: Tracks macro-level KPIs such as the Total Loan Amount ($312.43M) and the baseline Default Ratio (21.82%). Evaluates how default rates vary by specific Loan Intentions, highlighting Debt Consolidation at 28.59%.

<img width="1538" height="870" alt="image" src="https://github.com/user-attachments/assets/d21013c2-f3aa-46cb-b8ff-9b5651bba37a" />

---

### 👥 Borrowers Profiles Analysis

  * **Purpose**: Breaks down the demographic and professional backgrounds of the client base to uncover vulnerable borrower segments.
  * **Key Analysis**: Correlates the default ratio against income, employment type, and housing status. Features a Pareto Analysis illustrating that approximately 20% of customer groups are responsible for 80% of the total value of overdue debt.

<img width="1542" height="875" alt="image" src="https://github.com/user-attachments/assets/d3b8cded-99fa-4b54-8912-72ded965ad2e" />

---

### 💳 Loan Characteristic & Risk

  * **Purpose**: Examines how structural loan elements (grades, interest rates, terms) correlate with portfolio risk.
  * **Key Analysis**: Maps the Total Clients & Default Rate by Grade, demonstrating a steep risk curve. Tracks a High Risk Ratio of 15.02% and Total Other Debts amounting to $376.90M.

<img width="1540" height="881" alt="image" src="https://github.com/user-attachments/assets/dba1c888-4fa9-410e-9566-b3d79227e1b5" />

---

### ⚠️ Financial Health & Warning

  * **Purpose**: Acts as an early warning system by monitoring the debt burden and credit history of active borrowers.
  * **Key Analysis**: Analyzes default rates against History of Use Credit & Delinquencies. Identifies critical warning zones by mapping the DTI group against default likelihood. 

<img width="1541" height="875" alt="image" src="https://github.com/user-attachments/assets/70db5165-a276-4531-8ff8-a9f08bb1416a" />

---

### Modeling Approach

To transition from descriptive analytics to predictive insights, a machine learning pipeline was developed using Orange3 Data Mining software. The goal is to accurately classify high-risk loan applications before approval.

---

#### Model evaluation based on Test & Score table 

| Model | AUC | CA | F1 | Prec | Recall | MCC |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Logistic Regression** | 0.500 | 0.782 | 0.686 | 0.611 | 0.782 | 0.000 |
| **SVM** | 0.752 | 0.722 | 0.740 | 0.774 | 0.722 | 0.324 |
| **Random Forest** | 0.901 | 0.919 | 0.915 | 0.920 | 0.919 | 0.751 |

**Observation:**

* **Random Forest:** The absolute best performer across all metrics (AUC: 0.901, F1: 0.915, Prec: 0.919), showing exceptional and balanced classification ability.

* **SVM:** Achieved moderate results (AUC: 0.752), lacking the high reliability required for strict financial risk management.

* **Logistic Regression:** Performed the worst (AUC: 0.500, MCC: 0.000), proving to be no better than a random guess.

---

#### Model evaluation based on Confusion Matrix

* **Random Forest**

| Actual \ Predicted | 0 (Non-Default) | 1 (Default) | $\Sigma$ |
| :--- | :---: | :---: | :---: |
| **0 (Non-Default)** | 91.8% | 7.6% | **17831** |
| **1 (Default)** | 8.2% | 92.4% | **4976** |
| **$\Sigma$** | **19116** | **3691** | **22807** |

**Observation:**

* Accurately identified 92.4% of actual defaults within its high-risk predictions, making it highly effective at minimizing financial loss.

* Correctly classified 91.8% of non-default cases, maintaining a low false-alarm rate (7.6%) to ensure good customers are not wrongly rejected.
  
---

* **Support Vector Machine (SVM)**

| Actual \ Predicted | 0 (Non-Default) | 1 (Default) | $\Sigma$ |
| :--- | :---: | :---: | :---: |
| **0 (Non-Default)** | 87.6% | 59.0% | **17831** |
| **1 (Default)** | 12.4% | 41.0% | **4976** |
| **$\Sigma$** | **15312** | **7495** | **22807** |

**Observation:**

* High False Alarms: 59.0% of its default predictions were actually safe customers. This would lead the bank to reject a massive amount of good loan applications.

* Poor Risk Catch Rate: When predicting a default, it was only correct 41.0% of the time, making it unfit for a risk-averse business.

---

* **Logistic Regression**

| Actual \ Predicted | 0 (Non-Default) | 1 (Default) | $\Sigma$ |
| :--- | :---: | :---: | :---: |
| **0 (Non-Default)** | 78.2% | NA | **17831** |
| **1 (Default)** | 21.8% | NA | **4976** |
| **$\Sigma$** | **22807** | **0** | **22807** |

**Observation:**

* Complete Underfitting: The model failed entirely by predicting every single application as "safe" (Class 0), completely ignoring all actual defaults.

* Misleading Accuracy: The 78.2% accuracy it achieved merely reflects the natural distribution of safe customers in the original dataset. The model learned absolutely nothing about distinguishing between the two classes.

--- 

#### Model evaluation based on ROC Curve

<img width="2551" height="1508" alt="image" src="https://github.com/user-attachments/assets/2c4f984a-d87e-488c-aae7-90a1ab1fe556" />

**Observation:**

* **Random Forest:** The curve bows closest to the top-left corner, visually confirming it has the highest Area Under the Curve (AUC) and is the most robust model for distinguishing between default and non-default applications.
  
* **Support Vector Machine - SVM:** Sits entirely below the Random Forest curve, indicating moderate predictive power but demonstrating a clear performance gap compared to the leading model.
  
* **Logistic Regression:** Perfectly aligns with the diagonal baseline of random chance. This visually reinforces its complete inability to discriminate between safe and risky loans, rendering it practically useless for this dataset.

---

## 💡Key Findings

**Loan Portfolio Overview and Systemic Risk:**
* The total loan amount reaches $312.43 million, however, the overall default ratio remains quite high at 21.82%.
* The Loan Grade system reflects risk very accurately: The default rate for Grade A is under 10% (specifically 8.99%), but surges to 98.44% for Grade G.

**Impact of Income and Debt Burden (DTI):**
* The Debt-to-Income (DTI) ratio is an extremely strong risk indicator; when the DTI exceeds 40%, the default rate jumps to a highly dangerous level between 74.32% and 81.48%.
* Clients with an annual income below $30,000 have a default rate surging to 47.07%. 

**Loan Intention:**
* Loans used for "Debt Consolidation" pose the highest risk, leading with a default rate of 28.59%.
* This is followed by loans for Medical purposes at 26.70% and Home Improvement at 26.10%

**Customer Behavior and Pareto Principle (80/20:)**
* The highest risk segment (40% - 80% default rate) is concentrated in part-time workers or the unemployed who rent their homes.
* However, in terms of absolute value, approximately 20% of the customer groups are responsible for 80% of the total bad debt value; notably, the majority of this bad debt originates from full-time employees who are renting or have a mortgage.

---

## 🚀 Strategic Recommendations & Action Plan

**Tighten Underwriting Policies**
* Establish automated rejection rules or mandate additional collateral for loan applications with a Debt-to-Income (DTI) ratio exceeding 40% to mitigate the severe default risk of 74% - 81%.
* Immediately halt the disbursement of new loans for the extreme-risk segment classified as Grade G.
* Enforce stricter financial verification processes for highly vulnerable segments, specifically targeting part-time workers or unemployed individuals who are currently renting their homes.

**Apply Risk-Based Pricing**
* Increase interest rates or lower the maximum credit limits for loans intended for "Debt Consolidation" to compensate for the high-risk nature of this group.

**Collection Optimization**
* Instead of spreading efforts thin, the debt collection department should redirect 80% of its operational resources to focus on the 20% of customers who create the highest-value risk impact.
* Prioritize the close monitoring of full-time employees who are currently renting or paying off a mortgage, as this group generates the largest bad debt burden in terms of total value.

---

## 📁 Repository Structure

```text
📦 Credit-Risk-Analytics
├── 📂 datasets
│   ├── dataset.csv                          # Original dataset
│   ├── data for ML                          # Cleaned dataset for Machine Learning
│   └── data_dictionary.xlsx                 # Data dictionary
│
├── 📂 images
│   ├── information.png                      # Information page screenshot
│   ├── business_overview.png                # Business Overview dashboard screenshot
│   ├── borrowers_profiles_analysis.png      # Borrowers Profiles Analysis screenshot
│   ├── loan_characteristic_risk.png         # Loan Characteristic & Risk screenshot
│   ├── financial_health_warning.png         # Financial Health & Warning screenshot
│   ├── orange_workflow.png                  # Orange workflow screenshot
│
├── Credit_Risk_Dashboard.pbix               # Power BI dashboard file
│
├── credit_risk_model.ows                    # Orange machine learning workflow
│
└── 📄 README.md                             # Project documentation
```

---

## ✅ How to Use This Project

### Power BI Dashboard

1. Open the `.pbix` file using Power BI Desktop.
2. Navigate through the dashboard pages.
3. Use filters such as Country, Loan Term, Loan Grade, Employment Type, and House Ownership.
4. Analyze borrower segments, loan characteristics, and financial warning indicators.

### Orange Machine Learning Workflow

1. Open the `.ows` workflow file in Orange Data Mining.
2. Load the cleaned dataset.
3. Run the Test & Score widget to compare models.
4. Use Confusion Matrix and ROC Analysis to evaluate model performance.
5. Export prediction results if needed.

---

## 🏁 Final Conclusion

This project demonstrates how credit risk can be analyzed through both **business intelligence** and **machine learning**.

The Power BI dashboard provides a comprehensive view of portfolio performance, borrower risk profiles, loan characteristics, and financial warning signals. Meanwhile, the Orange machine learning workflow supports default prediction and model comparison.

The analysis shows that credit default risk is strongly influenced by borrower income, employment status, housing ownership, loan purpose, loan grade, and financial stress indicators such as DTI and LTI.

Among the tested machine learning models, **Random Forest performs best** and is recommended for credit default prediction.

---

Presenter: Tien Phap

Project Completion Date: 07/2026
