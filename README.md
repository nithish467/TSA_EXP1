# Ex.No: 01A PLOT A TIME SERIES DATA
###  Date: 01/11/2026

# AIM:
To develop a Python program to plot the time series data using the tesla_vehicle_sales_performance dataset and visualize the changes in Tesla vehicle sales over time.

# Dataset Name: 
tesla_vehicle_sales_performance.csv

# ALGORITHM:
1. Import the required packages such as Pandas and Matplotlib.
2. Read the tesla_vehicle_sales_performance dataset using Pandas.
3. Convert the order_date column into datetime format.
4. Select the order_date and net_revenue_usd columns from the dataset.
5. Group the net revenue data by month to calculate total monthly revenue.
6. Plot the time series data using a line graph.
7. Add a suitable title, X-axis label, Y-axis label and grid.
8. Display the graph.

# PROGRAM:
```python
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv('/content/tesla_vehicle_sales_performance.csv')
df['order_date'] = pd.to_datetime(df['order_date'])

# Group net revenue by month
monthly_revenue = df.groupby(
    df['order_date'].dt.to_period('M')
)['net_revenue_usd'].sum().reset_index()

monthly_revenue['order_date'] = monthly_revenue['order_date'].dt.to_timestamp()

plt.figure(figsize=(12, 6))

plt.plot(
    monthly_revenue['order_date'],
    monthly_revenue['net_revenue_usd'] / 1e6,
    color='#CC0000',
    marker='o',
    linewidth=2
)

plt.title('Tesla Total Monthly Net Revenue Trend',
          fontsize=14, fontweight='bold')

plt.xlabel('Date', fontsize=12)
plt.ylabel('Net Revenue (Millions USD)', fontsize=12)

plt.grid(True, linestyle='--', alpha=0.5)
plt.tight_layout()
plt.show()
```


# OUTPUT:
<img width="947" height="470" alt="image" src="https://github.com/user-attachments/assets/ea62afa5-5c87-4e3f-89d0-a95b487d15d0" />


# RESULT:
Thus, we have successfully created and executed a Python program to plot the time series data using the tesla_vehicle_sales_performance dataset. The graph clearly represents the changes in Tesla's total monthly net revenue over time.
