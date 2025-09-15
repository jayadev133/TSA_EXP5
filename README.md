# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 15/09/2025


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

file_path = "Coffe_sales.xlsx"   
data = pd.read_excel(file_path, sheet_name="index_1")

data["date"] = pd.to_datetime(data["date"])
daily_sales = (
    data.groupby("date")["money"]
    .sum()
    .sort_index()
)

daily_sales = daily_sales.asfreq("D")

daily_sales = daily_sales.fillna(0)

decomposition = seasonal_decompose(daily_sales, model="additive", period=30)

plt.figure(figsize=(10, 12))

plt.subplot(411)
plt.plot(daily_sales, label="Daily Coffee Sales")
plt.legend(loc="upper left")
plt.title("Daily Coffee Sales")

plt.subplot(412)
plt.plot(decomposition.trend, label="Trend", color="orange")
plt.legend(loc="upper left")
plt.title("Trend")

plt.subplot(413)
plt.plot(decomposition.seasonal, label="Seasonal", color="green")
plt.legend(loc="upper left")
plt.title("Seasonality")

plt.subplot(414)
plt.plot(decomposition.resid, label="Residual", color="red")
plt.legend(loc="upper left")
plt.title("Residuals")

plt.tight_layout()
plt.show()

```
### OUTPUT:
FIRST FIVE ROWS:



PLOTTING THE DATA:

SEASONAL PLOT REPRESENTATION :



TREND PLOT REPRESENTATION :

OVERAL REPRESENTATION:


<img width="990" height="1189" alt="TS EXP5 PIC" src="https://github.com/user-attachments/assets/545eb873-e43d-47ab-bf0f-40a9189badb3" />




### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
