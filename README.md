# Pareto Chart Tutorial (Example)

This tutorial demonstrates how to create Pareto charts using Python libraries like pandas, NumPy, and Matplotlib.

## What is a Pareto Chart?

A Pareto chart, also known as the 80/20 rule chart, is a visualization tool that combines a bar chart and a line chart. It reveals the distribution of a population of data. Typically, it highlights that a small portion (around 80%) of the factors contribute to a large portion (around 80%) of the outcome.

Here's a breakdown of the chart's components:

- __Bar chart:__ Represents categories or items on the x-axis and their corresponding frequencies or values on the y-axis.
- __Line chart:__ Shows the cumulative percentage of the values, plotted on a secondary y-axis.

Pareto charts are widely used in various fields, including quality control, business process improvement, and customer relationship management. They help identify areas for improvement by focusing on the factors contributing to the most significant impact.

You can use the following steps to create the Chart in Python:

### 1. Import Libraries:

```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

### 2. Prepare Data:
Create a pandas DataFrame with columns for complaint category and frequency.

```py
# Insert required data in a DataFrame
data = {'Category': ['Defect A', 'Defect B', 'Defect C', 'Defect D', 'Others'],
        'Frequency': [30, 20, 15, 5, 10]}

# Create pandas DataFrame
df = pd.DataFrame(data)

# Print the data
print("Raw Data:")
print(df.to_string(index=False))

# Create a table with the data
fig, ax = plt.subplots()
ax.axis('off')
ax.axis('tight')
ax.table(cellText=df.values, colLabels=df.columns, cellLoc='center', loc='center', colLoc='center')
plt.title('Defects Frequency')
plt.show()
```
### Sort Data in Descending Order:
```
# Sort DataFrame by frequency (descending)
df_sorted = df.sort_values(by=['Frequency'], ascending=False)

# Print sorted data
print("\nData sorted by Frequency (descending):")
print(df_sorted.to_string(index=False))

# Create a table with the sorted data
fig, ax = plt.subplots()
ax.axis('off')
ax.axis('tight')
ax.table(cellText=df_sorted.values, colLabels=df_sorted.columns, cellLoc='center', loc='center', colLoc='center')
plt.title('Defects Frequency (sorted)')
plt.show()
```
### Calculate Cumulative Percentage:
```
# Calculate cumulative sum of frequencies
df_sorted['Cumulative Percentage'] = df_sorted['Frequency'].cumsum() / df_sorted['Frequency'].sum() * 100

# Print data with cumulative percentages
print("\nData with Cumulative Percentages:")
print(df_sorted.to_string(index=False))

# Create a table with the data and cumulative percentages
fig, ax = plt.subplots()
ax.axis('off')
ax.axis('tight')
ax.table(cellText=df_sorted.values, colLabels=df_sorted.columns, cellLoc='center', loc='center', colLoc='center')
plt.title('Defects Frequency (sorted) with Cumulative Percentages')
plt.show()
```

### Create Pareto Chart:

```
# Create the figure and subplots
fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(10, 6))

# Bar chart for frequencies on primary axis (ax1)
ax1.bar(df_sorted['Category'], df_sorted['Frequency'], color='skyblue')
ax1.set_xlabel('Category')
ax1.set_ylabel('Frequency')
ax1.set_title('Frequency of Defects')

# Line chart for cumulative percentages on secondary axis (ax2)
ax2.plot(df_sorted['Category'], df_sorted['Cumulative Percentage'], color='red', marker='o', linestyle='-')
ax2.set_xlabel('Category')
ax2.set_ylabel('Cumulative Percentage (%)')
ax2.set_title('Cumulative Percentage of Defects')

# Set y-axis limits for cumulative percentages (0 to 100%)
ax2.set_ylim(0, 100)

# Rotate x-axis labels for better readability
plt.setp(ax1.xaxis.get_majorticklabels(), rotation=45)
plt.setp(ax2.xaxis.get_majorticklabels(), rotation=45)

# Display the plots
plt.tight_layout()
plt.show()

# Plot the bar chart with the frequencies and cummulative percentages
fig, ax1 = plt.subplots(figsize=(10, 6))
ax2 = ax1.twinx()
ax1.bar(df_sorted['Category'], df_sorted['Frequency'], color='skyblue')
ax2.plot(df_sorted['Category'], df_sorted['Cumulative Percentage'], color='red', marker='o', linestyle='-')
ax1.set_xlabel('Category')
ax1.set_ylabel('Frequency')
ax2.set_ylabel('Cumulative Percentage (%)')
ax1.set_title('Frequency and Cumulative Percentage of Defects')
plt.setp(ax1.xaxis.get_majorticklabels(), rotation=45)
plt.show()
```

This will give you a chart similar to the one given below:
![defects_frequency_cumulative_percentage_merged](https://github.com/HasanYahya101/Pareto-Tutorial-Python/assets/118683092/1321b072-9b53-40e6-b838-694342fc4220)

After that you can also save the image in an output file (such as png or jpeg).

### Note: 
All code for this is given in the __Jupyter Notebook__.

## License:

This repository is under the __MIT License__.
