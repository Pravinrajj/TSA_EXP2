# Ex.No: 02 LINEAR AND POLYNOMIAL TREND ESTIMATION
## DATE:
### AIM:
To Implement Linear and Polynomial Trend Estiamtion in XAUUAE Using Python.

### ALGORITHM:
Import necessary libraries (NumPy, Matplotlib)

Load the dataset

Calculate the linear trend values using least square method

Calculate the polynomial trend values using least square method

End the program
### PROGRAM:
```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Load the data
data = pd.read_csv('XAUUSD_2010-2023.csv')

# Convert date to datetime with the correct format and sort
data['Date'] = pd.to_datetime(data['time'], format='%d-%m-%Y %H:%M', dayfirst=True)
data.sort_values('Date', inplace=True)

# Filter data for a specific range (e.g., 1 year)
start_date = '2010-01-01'
end_date = '2011-01-01'
filtered_data = data[(data['Date'] >= start_date) & (data['Date'] <= end_date)]

# Extract date and price for the filtered range
dates = filtered_data['Date']
prices = filtered_data['close']

# Calculate linear trend
coeffs_linear = np.polyfit(np.arange(len(prices)), prices, 1)
linear_trend = np.polyval(coeffs_linear, np.arange(len(prices)))

# Calculate polynomial trend (degree 2)
coeffs_poly = np.polyfit(np.arange(len(prices)), prices, 2)
poly_trend = np.polyval(coeffs_poly, np.arange(len(prices)))

# Plotting
plt.figure(figsize=(12, 6))
plt.plot(dates, prices, color='blue', alpha=0.3, label='Original Data')  # Use transparency
plt.plot(dates, linear_trend, color='red', linewidth=2, label='Linear Trend')
plt.plot(dates, poly_trend, color='green', linewidth=2, label='Polynomial Trend (Degree 2)')
plt.xlabel('Date')
plt.ylabel('Price')
plt.title('Linear and Polynomial Trend Estimation (Shortened Data)')
plt.legend()
plt.show()

```

### OUTPUT
A - LINEAR TREND ESTIMATION
![image](https://github.com/user-attachments/assets/c066ffaf-566e-443c-9ca4-fcbfe0019e87)

B- POLYNOMIAL TREND ESTIMATION
![image](https://github.com/user-attachments/assets/e0d5955b-468b-44a3-97eb-79eb5e3c4213)

### RESULT:
Thus the python program for linear and Polynomial Trend Estiamtion in XAUUAE has been executed successfully.
