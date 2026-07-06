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

---

## 📊 Dashboard Architecture & Key Features

The Power BI dashboard is structured into **5 interactive pages**:

### 1. Information

The Information page introduces the project background, objectives, insight summary, and business recommendations.

- **Purpose:** Provides a high-level explanation of the credit risk analysis project.
- **Key Analysis:**
  - Defines project objectives.
  - Summarizes major risk insights.
  - Provides strategic recommendations for risk control.

![Information Page](<img width="1545" height="877" alt="image" src="https://github.com/user-attachments/assets/3ea206e7-8d60-44c4-9532-3f183fc5ff89" />
)

---











































