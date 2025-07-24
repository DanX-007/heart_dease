
# 🫀 Heart Disease Risk Prediction Model

A machine learning model to predict heart disease risk using SVM (Support Vector Machine).

## 📋 Model Specifications

| Component          | Details                                                                 |
|--------------------|-------------------------------------------------------------------------|
| **Algorithm**      | Support Vector Machine (SVM)                                            |
| **Kernel**         | Radial Basis Function (RBF)                                             |
| **Best Parameters**| `C=10.0`, `gamma='scale'`                                               |
| **Accuracy**       | 0.82 (5-fold cross validation)                                         |
| **Input Features** | 20 health parameters (see below)                                       |

## 📊 Input Parameters
All parameters must be provided in exact order:

| Parameter               | Type    | Description                              | Example Values        | Required |
|-------------------------|---------|------------------------------------------|-----------------------|----------|
| `Age`                   | float   | Patient's age in years                   | 45.0, 56.0           | ✅       |
| `Gender`                | string  | `"Male"` or `"Female"`                   | "Male"                | ✅       |
| `Blood Pressure`        | float   | Systolic BP (mmHg)                       | 120.0, 153.0         | ✅       |
| `Cholesterol Level`     | float   | Total cholesterol (mg/dL)                | 200.0, 155.0         | ✅       |
| `Exercise Habits`       | string  | `"High"`, `"Medium"`, `"Low"`            | "Medium"              | ✅       |
| `Smoking`               | string  | `"Yes"` or `"No"`                        | "No"                  | ✅       |
| `Family Heart Disease`  | string  | `"Yes"` or `"No"`                        | "Yes"                 | ✅       |
| `Diabetes`              | string  | `"Yes"` or `"No"`                        | "No"                  | ✅       |
| `BMI`                   | float   | Body Mass Index                          | 24.99, 28.5          | ✅       |
| `High Blood Pressure`   | string  | `"Yes"` or `"No"`                        | "No"                  | ✅       |
| `Low HDL Cholesterol`   | string  | `"Yes"` or `"No"`                        | "Yes"                 | ✅       |
| `High LDL Cholesterol`  | string  | `"Yes"` or `"No"`                        | "No"                  | ✅       |
| `Alcohol Consumption`   | string  | `"High"`, `"Medium"`, `"Low"`            | "Low"                 | ✅       |
| `Stress Level`          | string  | `"High"`, `"Medium"`, `"Low"`            | "Medium"              | ✅       |
| `Sleep Hours`           | float   | Average sleep duration (hours)           | 6.5, 7.63            | ✅       |
| `Sugar Consumption`     | string  | `"High"`, `"Medium"`, `"Low"`            | "Medium"              | ✅       |
| `Triglyceride Level`    | float   | Triglycerides (mg/dL)                    | 150.0, 342.0         | ✅       |
| `Fasting Blood Sugar`   | float   | Glucose level after fasting (mg/dL)      | 90.0, 110.0          | ❌       |
| `CRP Level`             | float   | C-reactive protein (mg/L)                | 0.8, 12.97           | ✅       |
| `Homocysteine Level`    | float   | Homocysteine (μmol/L)                    | 8.0, 12.39           | ✅       |

## 💻 Usage Example

from joblib import load
import pandas as pd

# Load model
model = load('heart_disease_model.joblib')

# Prepare input data (all 20 parameters required)
patient_data = pd.DataFrame([{
    'Age': 45.0,
    'Gender': 'Male',
    'Blood Pressure': 130.0,
    'Cholesterol Level': 220.0,
    'Exercise Habits': 'Medium',
    'Smoking': 'No',
    'Family Heart Disease': 'Yes',
    'Diabetes': 'No',
    'BMI': 26.5,
    'High Blood Pressure': 'No',
    'Low HDL Cholesterol': 'No',
    'High LDL Cholesterol': 'Yes',
    'Alcohol Consumption': 'Low',
    'Stress Level': 'Medium',
    'Sleep Hours': 6.5,
    'Sugar Consumption': 'Medium',
    'Triglyceride Level': 180.0,
    'Fasting Blood Sugar': 95.0,
    'CRP Level': 2.1,
    'Homocysteine Level': 9.8
}])

# Make prediction
risk = model.predict(patient_data)[0]
print("Heart Disease Risk:", "🔴 High" if risk == 1 else "🟢 Low")


## ⚠️ Important Notes
1. **Column Order Matters**: Input DataFrame must have exact same column order as above table
2. **Missing Values**: 
   - Numeric: Auto-filled with median
   - Categorical: Auto-filled with most frequent value
3. **New Categories**: Will be encoded as all zeros
4. **Data Types**: Must match specified types (float/string)

## 📈 Performance Metrics
| Metric        | Score  |
|---------------|--------|
| Accuracy      | 0.82   |
| Precision     | 0.83   |
| Recall        | 0.81   |
| F1-Score      | 0.82   |



Key features that make this display well on GitHub:
1. **Emoji headers** for visual scanning
2. **Compact tables** with clear borders
3. **Syntax highlighting** for code blocks
4. **Responsive design** works on mobile
5. **Required markers** (✅/❌) for parameters
6. **Color-coded** risk indicators

The markdown uses:
- Standard GitHub Flavored Markdown
- No HTML (which GitHub doesn't render)
- Consistent column widths
- Clear section separation
