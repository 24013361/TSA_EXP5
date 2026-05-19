# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 19-05-2026
### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:

```
# Imports
import os
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Show current folder
print("Current Directory:")
print(os.getcwd())

# Show files in folder
print("\nFiles:")
print(os.listdir())

# Load dataset
data = pd.read_csv(
    'chennai_temperature_10years.csv',
    parse_dates=['Date'],
    index_col='Date'
)

# Sort by date
data = data.sort_index()

# Preview dataset
print("\nFirst 5 Rows:")
print(data.reset_index().head())

# Convert daily data into monthly average
X = data['Temperature'].resample('ME').mean()

# Seasonal decomposition
decomposition = seasonal_decompose(
    X,
    model='additive',
    period=12
)

# Plot graphs
plt.figure(figsize=(12, 10))

# Original Data
plt.subplot(411)
plt.plot(X, linewidth=2)
plt.title('Monthly Average Chennai Temperature')
plt.grid(True)

# Trend
plt.subplot(412)
plt.plot(decomposition.trend, color='orange', linewidth=2)
plt.title('Smooth Trend Plot')
plt.grid(True)

# Seasonal
plt.subplot(413)
plt.plot(decomposition.seasonal, color='green', linewidth=2)
plt.title('Smooth Seasonality Plot')
plt.grid(True)

# Residual
plt.subplot(414)
plt.plot(decomposition.resid, color='red', linewidth=2)
plt.title('Residual Plot')
plt.grid(True)

plt.tight_layout()
plt.show()

```
### OUTPUT:
FIRST FIVE ROWS:

<img width="185" height="102" alt="image" src="https://github.com/user-attachments/assets/81a61e88-c8b5-4b65-b290-8d88ca352411" />


PLOTTING THE DATA:
<img width="1189" height="989" alt="image" src="https://github.com/user-attachments/assets/10f0791d-6f32-410e-9afb-f2fcd05fa27d" />


SEASONAL PLOT REPRESENTATION :

<img width="1189" height="989" alt="image" src="https://github.com/user-attachments/assets/c5c4d1ce-439c-4937-9bc0-d92376d8734d" />


TREND PLOT REPRESENTATION :
<img width="1189" height="989" alt="image" src="https://github.com/user-attachments/assets/be559a7d-5d8f-4c8d-889f-65a5dc3b2190" />


OVERAL REPRESENTATION:

<img width="1189" height="989" alt="image" src="https://github.com/user-attachments/assets/07636892-4357-40f0-a4c6-fd02011bd383" />


### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
