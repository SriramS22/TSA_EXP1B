# DEVELOPER NAME:Sriram S
# REG NO:212222240105
# DATE : 
# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
 

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on student performance data
### ALGORITHM:
```
1.Import the required packages like pandas and numpy
2.Read the data using the pandas
3.To remove any potential trends in the data
4.This step is applied if the data shows varying variance
5.If the data contains seasonality, subtract a rolling mean
6.Finally, check if the variables are stationary using the Augmented Dickey-Fuller (ADF) test
7.Display the overall results.
```

### PROGRAM:
```
import pandas as pd
df = pd.read_csv('student_performance.csv')
df.head()
print(df.head())

import matplotlib.pyplot as plt

df[['Attendance', 'StudyHours', 'PreviousGrade', 'FinalGrade']].plot(subplots=True, layout=(2, 2), figsize=(10, 8), title='Student Performance Metrics')
plt.show()
```

### differencing
```
df['Attendance_diff'] = df['Attendance'].diff().dropna()
df['StudyHours_diff'] = df['StudyHours'].diff().dropna()
df['PreviousGrade_diff'] = df['PreviousGrade'].diff().dropna()
df['FinalGrade_diff'] = df['FinalGrade'].diff().dropna()


df[['Attendance_diff', 'StudyHours_diff', 'PreviousGrade_diff', 'FinalGrade_diff']].plot(subplots=True, layout=(2, 2), figsize=(10, 8), title='Differenced Student Performance Metrics')
plt.show()
```

### Log Transformation
```

import numpy as np

df['Attendance_log'] = np.log(df['Attendance'])
df['StudyHours_log'] = np.log(df['StudyHours'])
df['PreviousGrade_log'] = np.log(df['PreviousGrade'])
df['FinalGrade_log'] = np.log(df['FinalGrade'])

df[['Attendance_log', 'StudyHours_log', 'PreviousGrade_log', 'FinalGrade_log']].plot(subplots=True, layout=(2, 2), figsize=(10, 8), title='Log-Transformed Student Performance Metrics')
plt.show()
```
# Seasonality Removal
```


rolling_mean_window = 2

df['Attendance_detrended'] = df['Attendance'] - df['Attendance'].rolling(window=rolling_mean_window).mean()
df['StudyHours_detrended'] = df['StudyHours'] - df['StudyHours'].rolling(window=rolling_mean_window).mean()
df['PreviousGrade_detrended'] = df['PreviousGrade'] - df['PreviousGrade'].rolling(window=rolling_mean_window).mean()
df['FinalGrade_detrended'] = df['FinalGrade'] - df['FinalGrade'].rolling(window=rolling_mean_window).mean()

df[['Attendance_detrended', 'StudyHours_detrended', 'PreviousGrade_detrended', 'FinalGrade_detrended']].plot(subplots=True, layout=(2, 2), figsize=(10, 8), title='Detrended Student Performance Metrics')
plt.show()
````





### OUTPUT:
# REGULAR DIFFERENCING:
![download](https://github.com/user-attachments/assets/b53ace7f-0c18-4931-9373-6d799be97748)
# SEASONAL ADJUSTMENT:
![download](https://github.com/user-attachments/assets/2d3e2a61-4c78-4760-8197-bdd5caca9620)
# LOG TRANSFORMATION:
![download](https://github.com/user-attachments/assets/629dee6a-6a32-4f7d-beec-33ed0ed5e70d)


### RESULT:
Thus  have created the python code for the conversion of non stationary to stationary data on student performance.
data.
