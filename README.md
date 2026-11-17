# Ex.No: 01A PLOT A TIME SERIES DATA
###  Date: 01/11/2026

# AIM:
To develop a Python program to plot the time series data using the AirPassengers dataset and visualize the changes in the number of air passengers over time.
### Dataset Name : AirPassengers
# ALGORITHM:
1. Import the required packages such as Pandas and Matplotlib.
2. Read the AirPassengers dataset using Pandas.
3. Convert the Month column into datetime format.
4. Select the Month and Passengers columns from the dataset.
5. Plot the time series data using a line graph.
6. Add a suitable title, X-axis label, Y-axis label and grid.
7. Display the graph.

# PROGRAM:
```
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv('/content/tesla_vehicle_sales_performance.csv')
df['order_date'] = pd.to_datetime(df['order_date'])

# Group net revenue by month to plot a clean time-series trend
monthly_revenue = df.groupby(df['order_date'].dt.to_period('M'))['net_revenue_usd'].sum().reset_index()
monthly_revenue['order_date'] = monthly_revenue['order_date'].dt.to_timestamp()

plt.figure(figsize=(12, 6))
plt.plot(monthly_revenue['order_date'], monthly_revenue['net_revenue_usd'] / 1e6, color='#CC0000', marker='o', linewidth=2)

plt.title('Tesla Total Monthly Net Revenue Trend', fontsize=14, fontweight='bold')
plt.xlabel('Date', fontsize=12)
plt.ylabel('Net Revenue (Millions USD)', fontsize=12)
plt.grid(True, linestyle='--', alpha=0.5)
plt.tight_layout()
plt.show()
```


# OUTPUT:
<img width="675" height="341" alt="image" src="https://github.com/user-attachments/assets/142bf785-ce9c-41bc-b683-a1167ff8c180" />


# RESULT:
Thus, we have successfully created and executed a Python program to plot the time series data using the AirPassengers dataset. The graph clearly represents the changes in the number of air passengers from 1949 to 1960.
