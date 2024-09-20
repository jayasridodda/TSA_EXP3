# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
## REGISTER NO: 212222240028
Date: 

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("Salesforcehistory.csv", nrows=35)
time_series = data['Open'] 

n_data_points = len(time_series)
n_lags = min(35, n_data_points - 1)
acf_values = np.zeros(n_lags)

mean = np.mean(time_series)
variance = np.var(time_series)
normalized_data = time_series - mean

for lag in range(n_lags):
    lagged_data = np.roll(normalized_data, -lag)
    acf_values[lag] = np.sum(normalized_data[:n_data_points-lag] * lagged_data[:n_data_points-lag]) / (variance * (n_data_points - lag))

plt.figure(figsize=(10, 6))
plt.stem(range(n_lags), acf_values)
plt.title(f'ACF Plot (Manual Calculation, Lags: {n_lags})')
plt.xlabel('Lag')
plt.ylabel('ACF')
plt.show()
```
### OUTPUT:
![image](https://github.com/user-attachments/assets/33682069-1ccc-4cba-a2b0-10daa389eaff)

### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
