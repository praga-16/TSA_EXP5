# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 


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
PRAGATHEESVARAN A B
212221240039
```
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Step 1: Load the dataset
data = pd.read_csv('AirPassengers.csv')

# Step 2: Convert 'Month' column to datetime format
data['Month'] = pd.to_datetime(data['Month'])

# Step 3: Set 'Month' as the index
data.set_index('Month', inplace=True)

# Step 4: Verify the exact column name
print(data.columns)

# Step 5: Perform seasonal decomposition using the correct column name
decomposition = seasonal_decompose(data['#Passengers'], model='additive')

# Step 6: Plot the decomposition
plt.figure(figsize=(10, 12))  # Adjust the figure size for a square shape

# Original Data
plt.subplot(411)
plt.plot(data['#Passengers'], label='Monthly Passengers')
plt.legend(loc='upper left')
plt.title('Monthly Passengers')

# Trend Plot
plt.subplot(412)
plt.plot(decomposition.trend, label='Trend', color='orange')
plt.legend(loc='upper left')
plt.title('Trend Plot')

# Seasonal Plot
plt.subplot(413)
plt.plot(decomposition.seasonal, label='Seasonal', color='green')
plt.legend(loc='upper left')
plt.title('Seasonal Plot')

# Residual Plot
plt.subplot(414)
plt.plot(decomposition.resid, label='Residual', color='red')
plt.legend(loc='upper left')
plt.title('Residual Plot')

plt.tight_layout()
plt.show()
```
# OUTPUT:

PLOTTING THE DATA:

![Untitled](https://github.com/user-attachments/assets/0facd4d3-b25f-49ef-99bc-d75d0aff53b1)

TREND PLOT REPRESENTATION :

![Untitled](https://github.com/user-attachments/assets/a639f4fe-cbfd-4de9-8e80-302be3d6f3fc)

SEASONAL PLOT REPRESENTATION :

![Untitled](https://github.com/user-attachments/assets/119b5e78-453a-4a2c-8152-2160e91097d8)

RESIDUAL PLOT :

![Untitled](https://github.com/user-attachments/assets/256c2db1-4d50-4de7-be67-f69541e3cef8)


### RESULT:
Thus, we have created the Python code for time series analysis and decomposition of the AirPassengers dataset, effectively extracting the trend, seasonal, and residual components to understand long-term growth and cyclical patterns in air travel.
