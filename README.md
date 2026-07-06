# **Deep-Dive Risk Analytics: Decoding the Roots of Bad Debt**

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

* **Outputs:** Final predictions were generated and exported to external data tables for further review[cite: 2].

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

### 👥 Borrowers Profiles Analysis**

  * **Purpose**: Breaks down the demographic and professional backgrounds of the client base to uncover vulnerable borrower segments.
  * **Key Analysis**: Correlates the default ratio against income, employment type, and housing status. Features a Pareto Analysis illustrating that approximately 20% of customer groups are responsible for 80% of the total value of overdue debt.

<img width="1542" height="875" alt="image" src="https://github.com/user-attachments/assets/d3b8cded-99fa-4b54-8912-72ded965ad2e" />

---

### 💳 Loan Characteristic & Risk**

  * **Purpose**: Examines how structural loan elements (grades, interest rates, terms) correlate with portfolio risk.
  * **Key Analysis**: Maps the Total Clients & Default Rate by Grade, demonstrating a steep risk curve. Tracks a High Risk Ratio of 15.02% and Total Other Debts amounting to $376.90M.

<img width="1540" height="881" alt="image" src="https://github.com/user-attachments/assets/dba1c888-4fa9-410e-9566-b3d79227e1b5" />

---

### ⚠️ Financial Health & Warning**

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


---

#### Model evaluation based on Confusion Matrix

* **Random Forest**

| Actual \ Predicted | 0 (Non-Default) | 1 (Default) | $\Sigma$ |
| :--- | :---: | :---: | :---: |
| **0 (Non-Default)** | 91.8% | 7.6% | **17831** |
| **1 (Default)** | 8.2% | 92.4% | **4976** |
| **$\Sigma$** | **19116** | **3691** | **22807** |

---

* **Support Vector Machine (SVM)**

| Actual \ Predicted | 0 (Non-Default) | 1 (Default) | $\Sigma$ |
| :--- | :---: | :---: | :---: |
| **0 (Non-Default)** | 87.6% | 59.0% | **17831** |
| **1 (Default)** | 12.4% | 41.0% | **4976** |
| **$\Sigma$** | **15312** | **7495** | **22807** |

---

* **Logistic Regression**

| Actual \ Predicted | 0 (Non-Default) | 1 (Default) | $\Sigma$ |
| :--- | :---: | :---: | :---: |
| **0 (Non-Default)** | 78.2% | NA | **17831** |
| **1 (Default)** | 21.8% | NA | **4976** |
| **$\Sigma$** | **22807** | **0** | **22807** |

--- 

#### Model evaluation based on ROC Curve









































