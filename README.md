#### DEVELOPED BY : SHARAN MJ
#### REG NO : 212222240097
#### DATE : 


# Ex.No: 02 LINEAR AND POLYNOMIAL TREND ESTIMATION
### AIM:
To Implement Linear and Polynomial Trend Estiamtion Using Python.

### ALGORITHM:
Import necessary libraries (NumPy, Matplotlib)

Load the dataset

Calculate the linear trend values using least square method

Calculate the polynomial trend values using least square method

End the program
### PROGRAM:
```py
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression
from sklearn.preprocessing import PolynomialFeatures
import numpy as np

from google.colab import drive
drive.mount('/content/drive')

data = pd.read_csv('/content/csv/AMZN.csv')

data['Date'] = pd.to_datetime(data['Date'])

# Check the column names and replace 'Min' with the correct name
print(data.columns)  # Print the available columns to verify
data['Min'] = data['Low'].fillna(data['Low'].mean()) # Assuming 'Low' is the correct column

X = np.array(data.index).reshape(-1, 1)
y = data['Min']

linear_regressor = LinearRegression()
linear_regressor.fit(X, y)
y_pred_linear = linear_regressor.predict(X)

poly = PolynomialFeatures(degree=2)
X_poly = poly.fit_transform(X)

poly_regressor = LinearRegression()
poly_regressor.fit(X_poly, y)
y_pred_poly = poly_regressor.predict(X_poly)


plt.figure(figsize=(35, 5))

# First subplot for the first 100 data points of 'Min' price
plt.subplot(1, 3, 1)
plt.plot(data['Date'].head(100), data['Min'].head(100), label='Price')
plt.xlabel('Date')
plt.ylabel('Price')
plt.title('Cost of Onion (First 100 Data Points)')
plt.grid(True)
plt.xticks(rotation=45)  # Rotate the x-axis labels for better readability
plt.tight_layout()  # Adjust layout for better spacing

# Show the plot
plt.show()

plt.figure(figsize=(35, 5))

# Second subplot for the first 100 data points (actual price and linear trend)
plt.subplot(1, 3, 2)
plt.plot(data['Date'].head(100), y[:100], label='Price')
plt.plot(data['Date'].head(100), y_pred_linear[:100], color='red', linestyle='--', label='Linear Trend')
plt.xlabel('Date')
plt.ylabel('Price')
plt.title('Linear Trend Estimation for Onion Price (First 100 Data Points)')
plt.legend()
plt.grid(True)
plt.xticks(rotation=45)  # Rotate x-axis labels for better readability
plt.tight_layout()  # Adjust layout for proper spacing

# Show the plot
plt.show()

plt.figure(figsize=(35, 5))

# Third subplot for the first 100 data points (actual price and polynomial trend)
plt.subplot(1, 3, 3)
plt.plot(data['Date'].head(100), y[:100], label='Actual Price')
plt.plot(data['Date'].head(100), y_pred_poly[:100], color='green', linestyle='--', label='Polynomial Trend (Degree 2)')
plt.xlabel('Date')
plt.ylabel('Price')
plt.title('Polynomial Trend Estimation for Onion Price (First 100 Data Points)')
plt.legend()
plt.grid(True)
plt.xticks(rotation=45)  # Rotate x-axis labels for better readability
plt.tight_layout()  # Adjust layout for proper spacing

# Show the plot
plt.show()
```
### OUTPUT

![Screenshot 2024-09-23 110737](https://github.com/user-attachments/assets/61fcf1d1-b6e4-4d35-a624-a9430b7fd315)


#### A - LINEAR TREND ESTIMATION

![Screenshot 2024-09-23 110757](https://github.com/user-attachments/assets/44bb02d8-3732-4c0f-9f21-4c16d25ba88c)


#### B- POLYNOMIAL TREND ESTIMATION
![Screenshot 2024-09-23 110809](https://github.com/user-attachments/assets/89d63c25-e22e-45fd-b846-40a4a60dd484)




### RESULT:
Thus the python program for linear and Polynomial Trend Estiamtion has been executed successfully.
