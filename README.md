# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
# Date: 2/9/2025
## Name: K KESAVA SAI
## Register Number: 212223230105
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
```py
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
price=pd.read_csv("Clean_Dataset.csv")

N=len(price)

## Define lags
lags = range(35)

## Pre-allocate autocorrelation table
autocorr_values = []

numeric_data = data.select_dtypes(include=np.number)
mean_data = numeric_data.mean()
variance_data = numeric_data.var()

## Normalize the data
normalized_data = (numeric_data - mean_data) / np.sqrt(variance_data)

## Go through lag components one-by-one
for col in numeric_data.columns:
    autocorr_values_col = []
    for lag in lags:
        if lag == 0:
            autocorr_values_col.append(1)  # Autocorrelation at lag 0 is always 1
        else:
            auto_cov = np.sum((numeric_data[col][:-lag] - mean_data[col]) * (numeric_data[col][lag:] - mean_data[col])) / N
            autocorr_values_col.append(auto_cov / variance_data[col])  # Normalize by variance
    autocorr_values.append(autocorr_values_col)

## Display the graph
plt.figure(figsize=(10, 6))
for i, col in enumerate(numeric_data.columns):
    plt.stem(lags, autocorr_values[i], label=col)
plt.title('Autocorrelation of Data')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.legend()
plt.grid(True)
plt.show()
```

### OUTPUT:
<img width="1285" height="638" alt="image" src="https://github.com/user-attachments/assets/41653813-800a-4c28-911a-3e039bee2f0b" />


### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
