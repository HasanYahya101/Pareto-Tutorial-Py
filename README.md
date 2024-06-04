# Pareto Chart Example Tutorial

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
