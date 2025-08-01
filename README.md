# IBM HR Employee Attrition Analysis Project
- An **exploratory data analysis** project using the **IBM HR Analytics Employee Attrition & Performance dataset** <br>
- Examines key HR metrics and employee characteristics to identify trends related to employee attrition

<br>

## Dataset

- **Source:** [IBM HR Analytics Employee Attrition & Performance Dataset](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset)
- **Format:** CSV
- **Records:** 1470 employees
- **Fields:** Attrition, Job Involvement, Job Role, Job Satisfaction, Number of Companies Worked, Over Time, Work Life Balance, Years At Company, Years In Current Role, etc.

<br>

## Tools Used

- Microsoft Excel

<br>

## Objectives

This case study aims to address the business problem of employee attrition by achieving the following objectives:

**Quantify the Attrition Problem**: To calculate the **overall attrition rate** and establish a benchmark for the company.

**Identify Attrition Drivers**: To use exploratory data analysis and visualization to identify key factors and employee segments most susceptible to attrition. This includes examining the impact of **tenure**, **career stability**, **job satisfaction**, and **work-life balance**.

**Generate Actionable Insights**: To synthesize the findings into a clear and concise summary that explains why employees are leaving and what trends are most influential.

**Provide Data-Driven Recommendations**: To conclude the analysis with specific, actionable recommendations designed to help the company mitigate attrition and improve employee retention.

<br>

## Defining the Business Problem

**Employee attrition** can result in substantial business costs, including recruitment expenses, extended training time for new hires, and the loss of valuable institutional knowledge. This project addresses that core business challenge by analyzing attrition trends within an organization.

The primary objective is to quantify the extent of employee attrition and identify the key factors driving it. To accomplish this, the analysis is guided by the following critical questions:

- **What is the overall attrition rate?** This provides a foundational metric against which future improvements can be benchmarked.

- **What are the key characteristics of employees who leave?** This analysis identifies high-risk employee segments based on factors like tenure, career history, and satisfaction levels.

- **What are the potential root causes of attrition?** The project investigates the relationship between attrition and key employee satisfaction metrics, such as **Job Satisfaction**, **Work-Life Balance**, and **Work Environment**, as well as other factors like **Overtime**.

By answering these questions with data, this project provides actionable insights that can be used to develop targeted strategies for improving employee retention.

<br>

## Data Cleaning

Although this dataset is claimed to be complete and free of inconsistencies, it was still examined for potential errors and irregularities.

<br>

- **Column Selection and Filtering**

This step involved identifying and removing columns from the raw dataset that were not relevant to the analysis of employee attrition. Removing unused columns makes the dataset easier to work with and helps keep the focus on the variables that matter for solving the business problem.

Columns that are placeholders, such as Employee Count, Over 18, and Standard Hours, were removed from the dataset because they didn’t offer meaningful insights into the factors affecting attrition.

<br>

- **Handling Missing Values and Data Validation**
  
No missing values were detected in the dataset. Excel's filter tool was used to verify this. The data was also checked for any misspellings. All numerical and categorical columns were confirmed to have the appropriate data types. Additionally, the dataset was examined for any leading or trailing whitespaces.

<br>

- **Feature Engineering and Key Metric Calculation**

**New Feature:** Average Working Years per Company

Calculation: This metric was calculated by dividing Total Working Years by Number of Companies Worked. However, some records showed a value of 0 for Number of Companies Worked. This likely means the employee has only ever worked at their current company, and the field reflects the number of previous companies. To avoid division by zero, we replaced the 0 with 1 in these specific cases, assuming their entire work experience is with this one company, so the metric becomes Total Working Years ÷ 1.

**Rationale**: This feature provides a more nuanced understanding of an employee's career stability, indicating their average tenure per employer.

<br>

**Key Metric**: Attrition Rate (%)

**Calculation**: The attrition rate was calculated as a summary statistic for each group (e.g., for each level of job satisfaction, each tenure bucket) using the formula: (Number of Yes responses) / (Total number of responses).

The standard attrition rate formula is: number of employees who left divided by the average number of employees. However, for the IBM HR Analytics dataset, which is usually a static snapshot that includes employees who left during a specific period, the simplified formula is commonly used and generally acceptable. This is because the total dataset size serves as the baseline for measuring attrition.

**Rationale**: This metric allows for a direct comparison of attrition likelihood across different employee segments.

<br>

## Data Analysis and Visualization

This section is divided into four parts:

1. Overall Attrition Overview
2. Impact of Key Factors on Attrition
3. Employee Tenure and Career Stability
4. Employee Satisfaction and Work Environment

<br>

- ### Attrition Overview

The overall attrition rate offers a basic insight into employee turnover within the company. 

<br>

<img width="532" height="414" alt="Employee Attrition Breakdown" src="https://github.com/user-attachments/assets/e44a8918-70ef-49ee-a3ff-c3b3859656bf" /> <br>

With an attrition rate of 16%, roughly one in six employees leave the organization. This underscores the importance of identifying and addressing the key factors driving turnover.<br>

<br>

- ### Impact of Key Factors on Attrition

Some workplace factors, such as **working overtime**, seem to strongly influence an employee’s decision to leave the company.

<br>

<img width="532" height="292" alt="Attrition vs Overtime" src="https://github.com/user-attachments/assets/bc5c5785-413e-40da-a4d5-ca83d2acb67a" /><br>

  
Employees who work overtime are much more likely to leave, with an attrition rate of **31%**. In contrast, those who don’t work overtime have a much lower attrition rate of **10%**. This means employees working overtime are over three times more likely to leave, suggesting that overtime could be a key factor contributing to employee turnover.

<br>

- ### Employee Tenure and Career Stability

<br>

<img width="532" height="308" alt="Employee Histogram" src="https://github.com/user-attachments/assets/ecfb78e3-2a3d-47d1-8d0c-27fc4ee2c8c3" /> <br>

The distribution of Years at the Company is heavily skewed toward shorter tenures, with most employees having been with the company for less than 8 years. This visual shows that while some employees have very long careers, the majority of the workforce consists of those with shorter stays.

<br>

<img width="532" height="308" alt="Attrition vs Number of Years" src="https://github.com/user-attachments/assets/725adc74-546f-4a0b-b188-cd263d8be19d" /><br>

This figure shows a steep decline in attrition as tenure increases, supporting the insights from the box plots. Attrition is highest at 30% among the newest employees with 0–2 years at the company. It drops to 14% for those with 3–5 years of service and continues to fall to just 6% for employees with 18–20 years at the company. This analysis highlights that the first few years are the most critical for improving employee retention.

<br>

<img width="532" height="346" alt="Attrition vs Number of Years (Plot)" src="https://github.com/user-attachments/assets/3508510b-60ea-4b79-8042-20137f558558" /> <br>

Employees who attrit tend to have significantly shorter overall tenures at the company. The median tenure for attrited employees is 2 years, compared to 3 years for those who remain. This indicates that a substantial portion of turnover occurs early in an employee's journey with the company.

<br>

<img width="532" height="346" alt="Attrition vs Current Role" src="https://github.com/user-attachments/assets/cbd18b40-ed4a-461b-b2a9-dad2b12075a1" /> <br>

Tenure in Current Role vs. Attrition: The same pattern holds true for time in a specific role. Employees who attrited had a shorter median time in their current role (2 years) compared to those who stayed (3 years). 

<br>

<img width="532" height="346" alt="Attrition vs Avg Working Years" src="https://github.com/user-attachments/assets/213d2578-8cc3-4fe4-bf7b-2e916be2471e" /> <br>

Career Stability vs. Attrition: A calculated metric, "Average Working Years Per Company," reveals that employees with a history of longer stays at previous companies are more likely to stay. The median for attrited employees is 2.1 years, while it's 5.0 years for those who did not attrit. This indicates that a history of "job hopping" is associated with a higher risk of attrition.

<br>

- ### Employee Satisfaction and Work Environment

<br>

<img width="532" height="292" alt="Attrition vs Job Satisfaction" src="https://github.com/user-attachments/assets/05597f8c-22cf-4595-bbae-f338b96b1ccf" /> <br>

Job Satisfaction: There is a clear link between job satisfaction and attrition. As job satisfaction increases from "Low" to "Very High," the attrition rate consistently decreases from 23% down to 11%. This shows that satisfied employees are significantly less likely to leave.

<br>

<img width="532" height="292" alt="Attrition vs Work Life Balance" src="https://github.com/user-attachments/assets/f851bb5c-a7b9-4df6-8ce4-a6d798c5c0e6" /> <br>

Work-Life Balance: Poor work-life balance is a major driver of attrition. The attrition rate for employees with a "Bad" rating is 31%. While better ratings generally decrease attrition, the lowest rate (14%) is observed for a "Good" rating (Level 3), and it slightly rises to 18% for the "Best" rating (Level 4). This suggests that a poor work-life balance is a major red flag, but a perfect balance isn't necessarily the single key to retention. 

<br>

<img width="532" height="292" alt="Attrition vs Environment Satisfaction" src="https://github.com/user-attachments/assets/c44217df-b484-4144-96a5-efd0b0c7c9c1" /> <br>

Environment Satisfaction: Similar to other satisfaction metrics, a poor work environment is a major risk. Employees with a "Low" rating have an attrition rate of 25%. The rate drops sharply to 15% for moderate satisfaction and continues to decrease slightly to 13% for very high satisfaction. This highlights that while a pleasant environment helps, a very negative one is particularly detrimental to retention. 

<br>

<img width="532" height="292" alt="Attrition vs Job Involvement" src="https://github.com/user-attachments/assets/16666875-c3c1-4a40-b886-193e8706ee07" /> <br>

There is a clear negative relationship between job involvement and attrition. Employees with low job involvement (Level 1) have a high attrition rate of 34%. As job involvement increases, the attrition rate drops steadily, reaching just 9% for those with very high involvement (Level 4). This highlights how important employee engagement is for improving retention.

## Conclusion and Recommendations

### Summary of Findings

The company has an overall attrition rate of 16%. The analysis reveals that attrition is strongly influenced by a few key factors:

- **Tenure and Stability**: Newer employees and those with a history of "job hopping" are significantly more likely to attrit.
- **Satisfaction and Engagement**: Low ratings for job involvement, job satisfaction, and work-life balance are all directly linked to higher attrition rates.
- **Overtime**: Employees who work overtime are more than three times as likely to leave the company, making this a critical factor in turnover.

### Recommendations

- **Focus on Early Retention**: Implement programs to support and engage new hires, as this is the highest-risk group for attrition.
- **Address Overtime**: Review and adjust company policies on overtime to reduce burnout and its associated high turnover.
- **Boost Satisfaction**: Invest in initiatives to improve job involvement and satisfaction, as these are strong deterrents to attrition.
- **Promote Work-Life Balance**: Actively support a healthy work-life balance to reduce attrition among a highly vulnerable segment of employees.







