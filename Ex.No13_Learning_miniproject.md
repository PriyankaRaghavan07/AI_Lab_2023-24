# Ex.No: 10 Machine Learning  
### DATE: 25/10/2025                                                                           
### REGISTER NUMBER : 212223060213
# Mental Health Prediction Using Machine Learning

## AIM
To predict whether an employee has a mental health issue based on workplace and personal factors (age, gender, family history, work interference, remote work) using a machine learning model.

## ALGORITHM
We will use Logistic Regression for binary classification (Yes/No).

Steps:
1. Load the dataset (`mental_health_dataset_large.xlsx`).  
2. Encode categorical features into numeric values using LabelEncoder.  
3. Split the dataset into training (80%) and testing (20%) sets.  
4. Train a Logistic Regression model on the training data.  
5. Predict the target variable (`Employee_Mental_Health`) for the test data.  
6. Calculate the accuracy score to evaluate model performance.  

## PROGRAM
```python
#Step 1: Upload your dataset in Colab

from google.colab import files
import pandas as pd

# This opens a file picker — choose your Excel file (e.g., mental_health_dataset_large.xlsx)
uploaded = files.upload()

# Get uploaded filename automatically
filename = next(iter(uploaded))
print("✅ File uploaded successfully:", filename)

# Read Excel into DataFrame
df = pd.read_excel(filename)
print("Dataset loaded successfully!")
print("Shape:", df.shape)
df.head()

# Step 2: Mental Health Prediction using Logistic Regression

from sklearn.model_selection import train_test_split
from sklearn.preprocessing import LabelEncoder
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score

# Encode categorical columns
label = LabelEncoder()
for col in df.columns:
    if df[col].dtype == 'object':
        df[col] = label.fit_transform(df[col])

# Features (X) and Target (y)
X = df.drop('Employee_Mental_Health', axis=1)
y = df['Employee_Mental_Health']

# Train-test split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Model training
model = LogisticRegression(max_iter=1000)
model.fit(X_train, y_train)

# Prediction
y_pred = model.predict(X_test)

# Accuracy
accuracy = accuracy_score(y_test, y_pred)
print("✅ Model Accuracy:", round(accuracy * 100, 2), "%")

# Step 3: View some test results
results = pd.DataFrame({
    'Actual': y_test,
    'Predicted': y_pred
})
results.head(10)
```
## Output
<img width="1282" height="362" alt="image" src="https://github.com/user-attachments/assets/a6b8a6fa-2db8-4d82-97f3-390df2be9e8f" />

<img width="691" height="60" alt="image" src="https://github.com/user-attachments/assets/2a89489e-9630-422f-b5f2-3584049c3243" />

<img width="338" height="676" alt="image" src="https://github.com/user-attachments/assets/90bf5551-6fa9-4af5-8c98-da28e93fae03" />

## Result:
The Logistic Regression model can successfully predict the probability of an employee having a mental health issue based on workplace factors and family history. The model achieved an accuracy of approximately 85%, indicating good predictive performance.





