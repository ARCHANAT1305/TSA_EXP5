# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 11/04/2025
#### NAME :ARCHANA T
#### REG NO: 212223240013


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
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
data = pd.read_csv('rainfall.csv')

date_cols = data.select_dtypes(include=['object', 'datetime']).columns
numeric_cols = data.select_dtypes(include=np.number).columns

data[date_cols[0]] = pd.to_datetime(data[date_cols[0]], errors='coerce')


data = data.dropna(subset=[date_cols[0]])


data.set_index(date_cols[0], inplace=True)
data = data.sort_index()


rainfall_col = numeric_cols[0]
data_limited = data[[rainfall_col]].iloc[:300]

decomposition = seasonal_decompose(data_limited[rainfall_col], model='additive', period=12)


plt.figure(figsize=(12, 4))
plt.plot(data_limited[rainfall_col], label='Rainfall')
plt.legend(loc='upper left')
plt.title('Rainfall (First 300 Entries)')
plt.show()

plt.figure(figsize=(12, 4))
plt.plot(decomposition.trend, label='Trend', color='orange')
plt.legend(loc='upper left')
plt.title('Trend Component')
plt.show()


plt.figure(figsize=(12, 4))
plt.plot(decomposition.seasonal, label='Seasonal', color='green')
plt.legend(loc='upper left')
plt.title('Seasonal Component')
plt.show()


plt.figure(figsize=(12, 4))
plt.plot(decomposition.resid, label='Residual', color='red')
plt.legend(loc='upper left')
plt.title('Residual Component')
plt.show()
```


















### OUTPUT:
![image](https://github.com/user-attachments/assets/05d6c875-a33d-4d9a-b1e4-7d487e5a9053)
![image](https://github.com/user-attachments/assets/bac2e9a5-b79a-4e23-ba97-46b2a192d709)
![image](https://github.com/user-attachments/assets/803a8795-f365-4e52-9d87-615149e6db2a)




### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
