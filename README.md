Introduction
Employee turnover is expensive, disruptive, and often avoidable if analyzed carefully. For our final project, we explored the IBM HR Analytics Employee Attrition dataset to understand why employees leave companies and how we can predict attrition before it occurs. Using Python, structured exploration, and modeling techniques, we aimed to build a predictive model that could assist HR teams in making informed retention decisions.
Understanding the Dataset
The IBM HR Analytics dataset provided a comprehensive snapshot of 1,470 employees, featuring 35 attributes related to demographics, work experience, compensation, and satisfaction levels.
The dataset was particularly valuable because it included a diverse set of features — not just obvious factors like salary, but also qualitative measures like job satisfaction and work-life balance.
Data Preparation: Data Cleaning
Before any modeling, it was essential to ensure that the dataset was clean and consistent. From our mid-project report, we made some changes in the one-hot encoding for better performance despite a more complex confusion matrix. Here are the major steps taken:
Missing Values: We checked for missing values using df.isnull().sum() and found none.
Duplicate Rows: No duplicate records were detected.
Redundant Columns: Certain columns, such as EmployeeCount, Over18, and StandardHours, contained constant values and were therefore removed.
Outlier Handling: Boxplots were used to identify outliers in variables like DistanceFromHome and MonthlyIncome. These were retained as they likely represented valid real-world cases.
Data Type Corrections: Categorical columns like Attrition and OverTime were converted to binary encoding. Numerical columns were correctly cast as integers or floats where appropriate.
Encoding Categorical Variables: One-hot encoding was applied to multi-class categorical variables such as Department and JobRole to ensure they were suitable for machine learning models.
After these steps, the dataset was ready for exploratory data analysis.
Exploring the Data: EDA (Exploratory Data Analysis)
Our exploratory analysis revealed several important patterns:
Attrition Rates: About 16% of employees had left the company.
Work-Life Balance: Employees reporting lower work-life balance were more likely to leave.
OverTime: Employees working overtime exhibited a higher attrition rate.
Monthly Income: Higher-paid employees tended to have lower attrition rates.
Years at Company: Newer employees (with fewer years at the company) showed higher turnover rates.
The correlation heatmap also confirmed expected relationships, such as the positive correlation between YearsAtCompanyand YearsInCurrentRole.

Outliers for individual features


Box Plots for Features vs Attrition

Box Plots for Features vs Attrition to visualise outliers

Correlation Heat Map
Building the Predictive Model: Logistic Regression
Given the binary nature of the target variable (Attrition), we selected Logistic Regression for its interpretability and effectiveness.
Selected features included:
Job Satisfaction
OverTime
Years at Company
Monthly Income
Percent Salary Hike
After splitting the dataset (80% training, 20% testing), we trained the initial model.
Initial Model Results:
Accuracy: ~85%
However, the model struggled to correctly predict instances of attrition.

Initial Model Performance Metrics

Initial Confusion Matrix
Class Imbalance Adjustment: By setting class_weight='balanced', we improved the model's ability to detect employees likely to leave.
Balanced Model Results:
Accuracy: ~73%
Precision: 22% (for attrition cases)
Recall: 41%

Final Model Performance Metrics

Final Confusion Matrix
Key Insights and Business Recommendations
Work-Life Balance and Overtime: Significant predictors of attrition. Companies should monitor workload and ensure a healthy work-life balance.
Salary Considerations: Employees with lower salaries showed higher attrition rates.
Employee Tenure: New hires are particularly vulnerable to turnover and may require additional engagement efforts.
For HR Teams:
Focus retention efforts on new employees.
Monitor overtime patterns to prevent burnout.
Address compensation disparities where feasible.
Future Work
Potential next steps include:
Exploring ensemble models like Random Forests or XGBoost for enhanced predictive performance.
Working with longitudinal datasets to analyze attrition trends over time.
Conclusion
This project highlighted the importance of careful data preparation, exploratory analysis, and appropriate modeling in understanding employee behavior. Predicting attrition is not just a technical exercise; it involves appreciating the human factors that drive workplace satisfaction and decisions.
The insights derived from this project can help organizations design targeted strategies to retain their valuable employees and foster a healthier work environment.
Thank you for reading!
