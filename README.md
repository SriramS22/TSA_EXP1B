### Developed by:Sriram S
### Reg no:212222240105
### Date:
# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international mulgrave river data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
3. Perform the Augmented Dickey-Fuller test on the original series.
4. Resample the data monthly, difference it again, and decompose it into seasonal components.
5. Remove the seasonal component and plot the seasonally adjusted series.
6. Apply a log transformation to the seasonally adjusted data and plot it.
### PROGRAM:


```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
from statsmodels.tsa.stattools import adfuller
df = pd.read_csv('/content/mulgrave.csv')
df
numeric_df = df.select_dtypes(include=[np.number])
numeric_df = numeric_df.dropna()
plt.figure(figsize=(10, 6))
numeric_df.plot()
plt.title('Original Non-Stationary Data')
plt.show()
df_diff = numeric_df.diff().dropna()
plt.figure(figsize=(10, 6))
df_diff.plot()
plt.title('Data after Regular Differencing')
plt.show()
from statsmodels.tsa.seasonal import seasonal_decompose

# Print the column names to check if 'datetime' exists
print(numeric_df.columns)

# Create a new column with the date information
numeric_df['datetime'] = pd.date_range(start='2022-01-01', periods=len(numeric_df), freq='D')

# Print the column names again to check if 'datetime' exists
print(numeric_df.columns)

# Set the 'datetime' column as the index
numeric_df.set_index('datetime', inplace=True)

# Specify the period of the time series data
period = 12  # For example, if the data is monthly

# Apply seasonal adjustment (e.g., using STL decomposition) to each column
for col in numeric_df.columns:
    decomposition = seasonal_decompose(numeric_df[col], model='additive', period=period)
    df_sa = decomposition.trend
    print(f"Seasonal decomposition for column {col}:")
    print(df_sa)
plt.figure(figsize=(10, 6))
df_sa.plot()
plt.title('Data after Seasonal Adjustment')
plt.show()
df_log = np.log(numeric_df)
plt.figure(figsize=(10, 6))
df_log.plot()
plt.title('Data after Log Transformation')
plt.show()
print("Original Data:")
print(numeric_df.describe())
print("\nData after Regular Differencing:")
print(df_diff.describe())
print("\nData after Seasonal Adjustment:")
print(df_sa.describe())
print("\nData after Log Transformation:")
print(df_log.describe())
```
### OUTPUT:

![Screenshot 2024-09-18 095002](https://github.com/user-attachments/assets/c7a674d4-1554-4a24-88e7-cfb0463cbdbc)


REGULAR DIFFERENCING:

![Screenshot 2024-09-18 095009](https://github.com/user-attachments/assets/f1513d43-5e2a-4d7a-938c-3ec0e55c0b3e)


SEASONAL ADJUSTMENT:

![Screenshot 2024-09-18 095019](https://github.com/user-attachments/assets/b87d10c2-5955-4899-a62b-32d1576fd033)


LOG TRANSFORMATION:
![Screenshot 2024-09-18 095026](https://github.com/user-attachments/assets/35482aaa-eb71-4e3d-8eee-7ae50059fdf6)



### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on mulgrave river
data.
