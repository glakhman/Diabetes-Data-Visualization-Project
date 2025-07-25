# 🩺 Project 1: Diabetes Data Visualization

## 📌 Introduction to the Problem

Diabetes is a serious health condition that affects millions worldwide. Early detection and lifestyle management can reduce its impact.  
This project explores which health indicators (like **glucose**, **BMI**, and **blood pressure**) show strong relationships with diabetes.

### ❓ Questions Asked
- What features show significant differences between diabetic and non-diabetic individuals?
- Are there patterns or trends in age, glucose levels, and other factors that help us understand the risk?

---

## 📊 Introduction to the Data

**Dataset Used:** [Kaggle Diabetes Dataset](https://www.kaggle.com/datasets/akshaydattatraykhare/diabetes-dataset)

| Feature | Description |
|---------|-------------|
| Pregnancies | Number of times pregnant |
| Glucose | Plasma glucose concentration |
| BloodPressure | Diastolic blood pressure |
| SkinThickness | Triceps skin fold thickness |
| Insulin | Serum insulin |
| BMI | Body mass index |
| DiabetesPedigreeFunction | Score based on family history |
| Age | Age in years |
| Outcome | 1 = diabetic, 0 = non-diabetic |

---

## 🛠️ Preprocessing the Data

Several columns had invalid zero values. We replaced them with the median of non-zero values:

```python
cols_with_zeros = ['Glucose', 'BloodPressure', 'BMI']
for col in cols_with_zeros:
    df[col] = df[col].replace(0, df[col].median())

```
To better visualize trends across age, I created age group categories:

```python
def age_to_group(age):
    if age < 30:
        return '18-29'
    elif age < 40:
        return '30-39'
    elif age < 50:
        return '40-49'
    elif age < 60:
        return '50-59'
    else:
        return '60+'

df['AgeGroup'] = df['Age'].apply(age_to_group)
```
## 📊 Data Understanding & Visualizations

I used various plots to explore how each feature relates to diabetes:

### 🔹 Outcome Distribution:
- Shows more non-diabetic patients than diabetic.

### 🔹 Boxplots by Outcome:
- Diabetic patients generally had higher glucose and BMI values.

### 🔹 Lineplot: Glucose vs Pregnancies
- Glucose levels seem to rise with more pregnancies, especially in diabetics.

### 🔹 Correlation Heatmap:
- Glucose, BMI, and Age had the highest correlation with Outcome.

---

## 📖 Storytelling

The visual exploration told a compelling story:

- People with diabetes generally have higher glucose levels, BMI, and are often older.
- Pregnancies may influence glucose, especially in diabetic individuals.
- While correlations aren’t extremely strong, glucose levels stood out across all charts.

**Key risk indicators**: Glucose, BMI, and Age.

## 💡 Impact & Limitations

### ✅ Potential Positive Impact:
- These visual insights can guide doctors and health professionals in identifying high-risk individuals.

### ⚠️ Possible Limitations & Harm:
- Dataset only includes females — results may not generalize.
- Bias or misinterpretation of health metrics may lead to oversimplification of diabetes risk.

### 🔍 Missing Perspectives:
- No lifestyle data (e.g., diet, exercise, medication).
- No time-series info to track health changes over time.

---

## 📚 References

- [Diabetes Dataset (Kaggle)](https://www.kaggle.com/datasets/akshaydattatraykhare/diabetes-dataset)
- Seaborn & pandas documentation
