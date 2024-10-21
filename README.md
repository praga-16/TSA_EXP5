# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 


### AIM:
To Illustrates how to perform time series analysis and decomposition on the Gold Price Prediction.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
PRAGATHEESVARAN A B
212221240039
```
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Load the dataset
file_path = 'Gold Price Prediction.csv'  # Replace with your actual file path
data = pd.read_csv(file_path)

# Display the column names to verify
print("Column names in the dataset:", data.columns)

# Ensure the 'Date' column is in datetime format and set it as the index
data['Date'] = pd.to_datetime(data['Date'])  # Adjust if your date column is named differently
data.set_index('Date', inplace=True)

# Use the correct column name for decomposition
series = data['Price Today']  # Use 'Price Today' for seasonal decomposition

# Perform decomposition
decomposition = seasonal_decompose(series, model='additive', period=12)  # Adjust period as needed

# Plotting the decomposition
plt.figure(figsize=(12, 8))
decomposition.plot()
plt.suptitle('Seasonal Decomposition of Time Series', fontsize=16)
plt.show()

# Display overall results
trend = decomposition.trend
seasonal = decomposition.seasonal
residual = decomposition.resid

print("Trend Component:")
print(trend.dropna().head())  # Display first few values of the trend
print("\nSeasonal Component:")
print(seasonal.dropna().head())  # Display first few values of the seasonal
print("\nResidual Component:")
print(residual.dropna().head())  # Display first few values of the residual

```
# OUTPUT:

PLOTTING THE DATA:
TREND PLOT REPRESENTATION :
SEASONAL PLOT REPRESENTATION :
RESIDUAL PLOT :

![image](https://github.com/user-attachments/assets/b6e239cc-4370-4319-8f1d-735e5905d4b8)


### RESULT:
Thus, we have created the Python code for time series analysis and decomposition of the Gold Price Prediction.
