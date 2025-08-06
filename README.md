# IBM HR Employee Attrition Analysis
- An **exploratory data analysis** project using the **IBM HR Analytics Employee Attrition & Performance dataset** <br>
- Examines key HR metrics and employee characteristics to identify trends linked to why employees attrite

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

## Defining the Business Problem

**Employee attrition** can result in substantial business costs, including recruitment expenses, extended training time for new hires, and the loss of valuable institutional knowledge. This project addresses that core business challenge by analyzing attrition trends within an organization.

The primary objective is to quantify the extent of employee attrition and identify the key factors driving it. To accomplish this, the analysis is guided by the following questions:

- **What is the overall attrition rate?** This creates a baseline metric for measuring future improvements.

- **What are the key characteristics of employees who leave?** This analysis highlights employee groups at high risk of leaving, based on tenure, career background, and job satisfaction.

- **What are the potential root causes of attrition?** The project looks at how attrition relates to important employee satisfaction factors like **Job Satisfaction, Work-Life Balance, Work Environment**, and also considers **Overtime**.

By answering these questions with data, this project provides actionable insights that can be used to develop targeted strategies for improving employee retention.

<br>

## Data Cleaning

Although this dataset is claimed to be complete and free of inconsistencies, it was still examined for potential errors and irregularities.

### Column Selection and Filtering

This step involved identifying and removing columns from the raw dataset that were not relevant to the analysis of employee attrition. Removing unused columns makes the dataset easier to work with and helps keep the focus on the variables that matter for solving the business problem.

Columns that are placeholders, such as Employee Count, Over 18, and Standard Hours, were removed from the dataset because they didn’t offer meaningful insights into the factors affecting attrition.

<br>

### Handling Missing Values and Data Validation
  
No missing values were detected in the dataset. Excel's filter tool was used to verify this. The data was also checked for any misspellings. All numerical and categorical columns were confirmed to have the appropriate data types. Additionally, the dataset was examined for any leading or trailing whitespaces.

<br>

### Calculated Field and Key Metric Calculation<br>

**New Field 1:** **Average Working Years per Company**

This metric was calculated by dividing **Total Working Years** by **Number of Companies Worked**. However, some records showed a value of 0 for Number of Companies Worked. This likely means the employee has only ever worked at their current company, and the field reflects the number of previous companies. To avoid division by zero, we replaced the 0 with 1 in these specific cases, assuming their entire work experience is with this one company, so the metric becomes **Total Working Years ÷ 1**.

**Basis**: This feature provides a more nuanced understanding of an employee's career stability, indicating their average tenure per employer.
  
  <br>

**New Field 2:** **Age Group**

The age data is binned into groups to be used as a filter.

  <br>
  
**Key Metric**: **Attrition Rate (%)**
  
The attrition rate was calculated as a summary statistic for each group (e.g., for each level of job satisfaction, each tenure bucket) using the formula: **Number of Yes responses / Total number of responses**.
Two new columns were derived from the Attrition column to enable the calculation of the attrition rate in pivot tables. The columns' names are **IsYes** and **IsNo**, containing binary numbers 1 and 0. IsYes contains 1 for "Yes", and 0 for "No"; and vice versa for IsNo.<br>

The standard attrition rate is calculated by dividing the number of employees who left by the average number of employees. But in the IBM HR Analytics dataset, a simplified formula is commonly used. This works because the total dataset is a static snapshot, including only a specific period that is not available in the dataset.

**Basis**: This metric allows for a direct comparison of attrition likelihood across different employee segments.

<br>

## Data Analysis and Visualization

This section is divided into three parts:

1) Overall Attrition Overview
2) Employee Tenure and Career Stability
3) Employee Satisfaction and Work Environment

<br>

### 1) Attrition Overview

<br>

<img width="400" height="300" alt="Employee Attrition Breakdown" src="https://github.com/user-attachments/assets/e44a8918-70ef-49ee-a3ff-c3b3859656bf" /> <br>

With an attrition rate of **16%**, roughly one in six employees leave the organization. This underlines the importance of identifying and addressing the key factors driving attrition.<br>

<br>

### 2) Employee Tenure and Career Stability

<br>

<img width="532" height="308" alt="Employee Histogram" src="https://github.com/user-attachments/assets/ecfb78e3-2a3d-47d1-8d0c-27fc4ee2c8c3" /> <br>


**Employee Tenure**: he distribution of **years at the company** is heavily skewed toward shorter tenures. Most employees don’t stay very long. Around **600** have worked at the company for **0–4 years**. That number drops to **400** for **4–8 years**, **200** for **8–12 years**, and fewer than **100** for each group after that, up to **36–40 years**. This shows that short stays are much more common than long ones.


<br>

<img width="475" height="300" alt="image" src="https://github.com/user-attachments/assets/57946532-8643-4ded-9599-b91424c904c5" />
<img width="400" height="300" alt="Attrition vs Number of Years (Plot)" src="https://github.com/user-attachments/assets/3508510b-60ea-4b79-8042-20137f558558" /> <br>

<br>

The first few years are the most critical for improving employee retention. This figure shows a steep decline in attrition as working years at the company increase. Attrition is **highest at** **30%** among the newest employees with **0–2 years** at the company. It drops to **14%** for those with **3–5 years** of service and continues to fall to just **6%** for employees with **18–20** years at the company. 

**The box plot** supports the insights from the bar chart. The employees who have been with the company longer are more likely to stay. For those who left, the typical stay was only **3 years**. For those who stayed, it was **6 years**. This suggests that newer employees are at a higher risk of leaving.

<br>

<img width="532" height="346" alt="Attrition vs Avg Working Years" src="https://github.com/user-attachments/assets/213d2578-8cc3-4fe4-bf7b-2e916be2471e" /> <br>

**Career Stability and Attrition**: A calculated field, **Average Working Years Per Company**, shows that employees who stayed longer at their previous jobs are more likely to stay with the company now. For people who **left**, the typical stay at previous jobs was only **2.1 years**. For those who **stayed**, it was **5 years**. This suggests that employees with a pattern of job hopping are at a higher risk of leaving.

<br>

### 3) Employee Satisfaction and Work Environment

<br>

<img width="532" height="292" alt="Attrition vs Job Satisfaction" src="https://github.com/user-attachments/assets/05597f8c-22cf-4595-bbae-f338b96b1ccf" /> <br>

**Job Satisfaction**: Employees who are happier with their jobs are much less likely to leave. When job satisfaction is rated as “Low,” the attrition rate is **23%**. As satisfaction improves to “Very High,” the rate drops to just **11%**. This clearly shows that keeping employees satisfied plays a big role in reducing attrition.

<br>

<img width="532" height="292" alt="Attrition vs Work Life Balance" src="https://github.com/user-attachments/assets/f851bb5c-a7b9-4df6-8ce4-a6d798c5c0e6" /> <br>

**Work-Life Balance**: When employees feel they don’t have a good balance between work and personal life, they’re much more likely to leave. Those with a “**Bad**” rating have a high attrition rate of **31%**. Attrition drops to its lowest point, **14%** at the “**Good**” level (Level 3), but then rises slightly to **18%** at the “**Best**” level (Level 4). This shows that while poor balance is a clear risk, having a perfect balance isn’t the only thing that keeps people from leaving.

<br>

<img width="532" height="292" alt="Attrition vs Overtime" src="https://github.com/user-attachments/assets/bc5c5785-413e-40da-a4d5-ca83d2acb67a" /><br>

**Overtime**: Employees who work overtime are much more likely to leave, with an attrition rate of **31%**. In contrast, those who don’t work overtime have a much lower attrition rate of **10%**. This means employees working overtime are over three times more likely to leave, suggesting that overtime could be a key factor contributing to employee turnover.

<br>

<img width="532" height="292" alt="Attrition vs Environment Satisfaction" src="https://github.com/user-attachments/assets/c44217df-b484-4144-96a5-efd0b0c7c9c1" /><br>


**Satisfaction with the Work Environment**: A bad work environment makes people much more likely to leave. Employees who rate it as “Low” have a **25%** attrition rate. This drops to **15%** for moderate satisfaction and **13%** for very high satisfaction. While a great environment helps, avoiding a negative one is especially important for keeping employees.

<br>

<img width="532" height="292" alt="Attrition vs Job Involvement" src="https://github.com/user-attachments/assets/16666875-c3c1-4a40-b886-193e8706ee07" /> <br>

**Job Involvement**: There’s a clear pattern showing that employees who don’t feel very involved in their work are much more likely to leave the company. For example, people with the lowest level of job involvement (Level 1) have a high attrition rate of **34%**. But as employees feel more connected and involved in their work, fewer of them leave. At the highest level of involvement (Level 4), the attrition rate drops to just **9%**. This shows that helping employees feel more engaged in their jobs can make a big difference in keeping them with the company.

<br>

## Conclusion and Recommendations

### Summary

The company’s overall employee attrition rate is **16%**. After looking closely at the data, we found that people tend to leave the company for a few main reasons:

- **Tenure and Work History**: Employees who are new to the company or have switched jobs often in the past are much more likely to leave. This shows that people who haven’t stayed long in jobs before may be at higher risk of leaving again.

- **How They Feel About Their Work**: People who gave low scores for job satisfaction, how involved they feel in their work, or how well they can balance work with personal life were more likely to quit. This means that when employees aren’t happy or don’t feel connected to their job, they’re more likely to leave.

- **Working Overtime**: Employees who regularly work overtime are more than three times more likely to quit than those who don’t. This shows that working long hours is a major reason people decide to leave, and it’s something the company should look into carefully.

### Recommendations

- **Pay special attention to new employees**: Create programs that help new workers feel welcome, supported, and part of the team. People who are new to the company are the most likely to leave, so it’s important to make sure they have a positive beginning.

- **Take a close look at overtime**: Go over the rules and practices around working extra hours. Working too much can lead to stress and feeling worn out, which makes people more likely to quit. Making changes here can help people feel better and stay longer.

- **Make the job more enjoyable**: Spend time and money on ways to help employees enjoy their work and feel more connected to what they do. When people feel good about their jobs, they’re less likely to leave.

- **Help people balance work and life**: Encourage a balance between work and personal life. When employees feel like they have time for themselves and their families, they’re more likely to stay. This is especially important for groups of employees who are already feeling overwhelmed.
<br>

## Dashboard


<img width="3854" height="1963" alt="HR Dashboard8" src="https://github.com/user-attachments/assets/f76f232f-7e41-4407-b40e-ca95b23f3458" />












