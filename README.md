# Exploring Mental Health Data

The small project to explore the basic concepts of machine learning. The goal is to use data from a mental health survey to explore factors that may cause individuals to experience depression.

## Getting Started
## 1. Understanding the task
### 1.1 What are you trying to predict (target variable)?

We are trying to predict whether a person is suffering from depression (Depression). This is a binary variable, with values 0 (no depression) or 1 (depression present).

### 1.2 What are the evaluation metrics?

The results are evaluated using accuracy. This means the model will be assessed based on the percentage of correct predictions out of the total examples in the test dataset.

### 1.3 What is the format of the input and output data?

**Input Data:**
A table with various columns such as:
- id: A unique identifier for each record.
- Demographic data (age, gender, city).
- Work/education-related attributes (CGPA, Work Pressure, Academic Pressure).
- Other personal data (e.g., Sleep Duration, Dietary Habits).
  
**_The dataset contains missing values that need to be handled!_**
  
**Output Data (submission.csv):**
A file with two columns:
- id: The identifier for the row from the test dataset.
- Depression: The predicted value (0 or 1).
- Format example:
```
id,Depression
140700,0
140701,0
140702,1
```
