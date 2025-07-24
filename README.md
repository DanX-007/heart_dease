<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Heart Disease Prediction Model Documentation</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            max-width: 900px;
            margin: 0 auto;
            padding: 25px;
            color: #333;
        }
        h1 {
            color: #2c3e50;
            border-bottom: 2px solid #3498db;
            padding-bottom: 8px;
        }
        h2 {
            color: #2980b9;
            margin-top: 25px;
        }
        code {
            background: #f8f9fa;
            padding: 2px 6px;
            border-radius: 3px;
            font-family: 'Consolas', monospace;
        }
        pre {
            background: #f8f9fa;
            padding: 12px;
            border-left: 4px solid #3498db;
            border-radius: 3px;
            overflow-x: auto;
        }
        .note {
            background: #e7f5fe;
            padding: 12px;
            border-left: 4px solid #3498db;
            margin: 15px 0;
            border-radius: 3px;
        }
        .parameter-table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
            font-size: 14px;
        }
        .parameter-table th {
            background-color: #3498db;
            color: white;
            text-align: left;
        }
        .parameter-table th, .parameter-table td {
            border: 1px solid #ddd;
            padding: 10px 12px;
            vertical-align: top;
        }
        .parameter-table tr:nth-child(even) {
            background-color: #f9f9f9;
        }
        .required {
            color: #e74c3c;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <h1>Heart Disease Risk Prediction Model</h1>

    <h2>Model Specifications</h2>
    <div class="note">
        <strong>Algorithm:</strong> Support Vector Machine (SVM) with RBF kernel<br>
        <strong>Best Parameters:</strong> C=10.0, gamma='scale'<br>
        <strong>Accuracy:</strong> 0.82 (5-fold cross validation)
    </div>

    <h2>Input Parameters</h2>
    <p>All parameters must be provided in a DataFrame with these exact column names:</p>
    
    <table class="parameter-table">
        <thead>
            <tr>
                <th>Parameter</th>
                <th>Type</th>
                <th>Description</th>
                <th>Example Values</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Age</td>
                <td>numeric</td>
                <td>Patient's age in years</td>
                <td>45, 56.0</td>
            </tr>
            <tr>
                <td>Gender</td>
                <td>string</td>
                <td>Patient's gender</td>
                <td>"Male", "Female"</td>
            </tr>
            <tr>
                <td>Blood Pressure</td>
                <td>numeric</td>
                <td>Systolic blood pressure (mmHg)</td>
                <td>120, 153.0</td>
            </tr>
            <tr>
                <td>Cholesterol Level</td>
                <td>numeric</td>
                <td>Total cholesterol (mg/dL)</td>
                <td>200, 155.0</td>
            </tr>
            <tr>
                <td>Exercise Habits</td>
                <td>string</td>
                <td>Frequency of exercise</td>
                <td>"High", "Medium", "Low"</td>
            </tr>
            <tr>
                <td>Smoking</td>
                <td>string</td>
                <td>Smoking status</td>
                <td>"Yes", "No"</td>
            </tr>
            <tr>
                <td>Family Heart Disease</td>
                <td>string</td>
                <td>Family history of heart disease</td>
                <td>"Yes", "No"</td>
            </tr>
            <tr>
                <td>Diabetes</td>
                <td>string</td>
                <td>Diabetes status</td>
                <td>"Yes", "No"</td>
            </tr>
            <tr>
                <td>BMI</td>
                <td>numeric</td>
                <td>Body Mass Index</td>
                <td>24.99, 28.5</td>
            </tr>
            <tr>
                <td>High Blood Pressure</td>
                <td>string</td>
                <td>Hypertension diagnosis</td>
                <td>"Yes", "No"</td>
            </tr>
            <tr>
                <td>Low HDL Cholesterol</td>
                <td>string</td>
                <td>Low HDL cholesterol status</td>
                <td>"Yes", "No"</td>
            </tr>
            <tr>
                <td>High LDL Cholesterol</td>
                <td>string</td>
                <td>High LDL cholesterol status</td>
                <td>"Yes", "No"</td>
            </tr>
            <tr>
                <td>Alcohol Consumption</td>
                <td>string</td>
                <td>Alcohol intake level</td>
                <td>"High", "Medium", "Low"</td>
            </tr>
            <tr>
                <td>Stress Level</td>
                <td>string</td>
                <td>Perceived stress level</td>
                <td>"High", "Medium", "Low"</td>
            </tr>
            <tr>
                <td>Sleep Hours</td>
                <td>numeric</td>
                <td>Average sleep duration (hours)</td>
                <td>6.5, 7.63</td>
            </tr>
            <tr>
                <td>Sugar Consumption</td>
                <td>string</td>
                <td>Dietary sugar intake</td>
                <td>"High", "Medium", "Low"</td>
            </tr>
            <tr>
                <td>Triglyceride Level</td>
                <td>numeric</td>
                <td>Triglycerides (mg/dL)</td>
                <td>150, 342.0</td>
            </tr>
            <tr>
                <td>Fasting Blood Sugar</td>
                <td>numeric</td>
                <td>Glucose level after fasting (mg/dL)</td>
                <td>90, 110 (null allowed)</td>
            </tr>
            <tr>
                <td>CRP Level</td>
                <td>numeric</td>
                <td>C-reactive protein (mg/L)</td>
                <td>0.8, 12.97</td>
            </tr>
            <tr>
                <td>Homocysteine Level</td>
                <td>numeric</td>
                <td>Homocysteine (μmol/L)</td>
                <td>8.0, 12.39</td>
            </tr>
        </tbody>
    </table>

    <div class="note">
        <strong>Note:</strong> The model automatically handles:
        <ul>
            <li>Missing values (median imputation for numeric features, mode for categorical)</li>
            <li>New categories in test data (encoded as all zeros)</li>
            <li>Feature scaling (standardization of numeric features)</li>
        </ul>
    </div>

    <h2>Usage Example</h2>
    <pre><code>from joblib import load
import pandas as pd

# Load model
model = load('heart_disease_model.joblib')

# Prepare input data
patient_data = pd.DataFrame([{
    'Age': 45,
    'Gender': 'Male',
    'Blood Pressure': 130,
    'Cholesterol Level': 220,
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
    'Triglyceride Level': 180,
    'Fasting Blood Sugar': 95,
    'CRP Level': 2.1,
    'Homocysteine Level': 9.8
}])

# Make prediction
risk = model.predict(patient_data)[0]
print("Heart Disease Risk:", "High" if risk == 1 else "Low")</code></pre>
</body>
</html>
