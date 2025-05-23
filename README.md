# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Initialize Parameters – Set initial values for slope m and intercept 𝑏 and choose a learning rate 𝛼
2. Compute Cost Function – Calculate the Mean Squared Error (MSE) to measure model performance.
3. Update Parameters Using Gradient Descent – Compute gradients and update m and b using the learning rate.
4. Repeat Until Convergence – Iterate until the cost function stabilizes or a maximum number of iterations is reached. 

## Program:
```
/*
Program to implement the linear regression using gradient descent.
Developed by: VISHAL S
RegisterNumber:  212224040364
*/
import numpy as np
import pandas as pd 
from sklearn.preprocessing import StandardScaler

def linear_regression(X1, y, learning_rate=0.1, num_iters=1000):
    X=np.c_[np.ones(len(X1)),X1]
    
    theta=np.zeros(X.shape[1]).reshape(-1,1)
    
    for _ in range(num_iters):
        predictions=(X).dot(theta).reshape(-1,1)
        
        errors=(predictions-y).reshape(-1,1)

        theta -=learning_rate*(1/len(X1))*X.T.dot(errors)
    return theta

data=pd.read_csv("/content/50_Startups.csv")
data.head()
X=(data.iloc[1:,:-2].values)
X1=X.astype(float)

scaler=StandardScaler()
y=(data.iloc[1:,-1].values).reshape(-1,1)
X1_Scaled=scaler.fit_transform(X1)
Y1_Scaled=scaler.fit_transform(y)
print(X)
print(X1_Scaled)
theta=linear_regression(X1_Scaled, Y1_Scaled)
new_data= np.array([165349.2 , 136897.8 , 471784.1]).reshape(-1,1)
new_scaled=scaler.fit_transform(new_data)
prediction=np.dot(np.append(1, new_scaled), theta)
prediction= prediction.reshape(-1,1)
pre = scaler.inverse_transform(prediction)
print(prediction)
print(f"Predicted value: {pre}")
```

## Output:

![Screenshot 2025-03-19 140325](https://github.com/user-attachments/assets/c7b26e98-94cc-40ea-aa48-452c49ae1ef3)
![Screenshot 2025-03-19 140414](https://github.com/user-attachments/assets/369de4e6-25ce-474d-b8f8-478c67b2f25e)
![Screenshot 2025-03-19 140443](https://github.com/user-attachments/assets/36ceb044-f3b0-4b4c-a14f-8b64d6ac532e)
![Screenshot 2025-03-19 140507](https://github.com/user-attachments/assets/7145041e-ab37-4710-97d0-4f2c237e6a21)
![Screenshot 2025-03-19 140551](https://github.com/user-attachments/assets/723c1c39-4718-46e2-acc7-83d241826f12)
![Screenshot 2025-03-19 140616](https://github.com/user-attachments/assets/0482e9d7-296d-4108-8936-e27d0bcf13eb)
![Screenshot 2025-03-19 140709](https://github.com/user-attachments/assets/729cb8e7-0303-4f91-8e19-82a3b4efccff)


## Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming.
