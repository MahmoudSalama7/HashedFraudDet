# HashedFraudDet


```markdown
# Fraud Detection Analysis

This project analyzes fraudulent transactions, focusing on the relationship between transaction amounts and the time of day. The dataset is divided into fraudulent (`fraud_df`) and non-fraudulent (`non_fraud_df`) transactions, with detailed visualizations to explore the data.

## Table of Contents
- [Project Overview](#project-overview)
- [Installation](#installation)
- [Data](#data)
- [Analysis](#analysis)
- [Results](#results)
- [Conclusion](#conclusion)
- [Contributing](#contributing)
- [License](#license)

## Project Overview
The goal of this project is to study patterns in fraudulent transactions by analyzing the distribution of transaction amounts across different times of the day. By examining these patterns, we aim to identify insights that could help in detecting fraud more effectively.

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/fraud-detection-analysis.git
   cd fraud-detection-analysis
   ```

2. Install the necessary dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Data
The data used in this project is divided into two dataframes:
- **`fraud_df`**: Contains records of fraudulent transactions.
- **`non_fraud_df`**: Contains records of non-fraudulent transactions.

The columns of interest include:
- **`Time`**: Time of the transaction (in seconds from the start of the day).
- **`Amount`**: Transaction amount in the dataset currency.
- **`Class`**: Indicates whether a transaction is fraudulent (`1`) or non-fraudulent (`0`).
- **`Time_of_Day`**: Derived feature that categorizes transactions into morning, afternoon, evening, or night.

## Analysis
### 1. Distribution of Transaction Amounts by Time of Day
The dataset is analyzed by binning transaction amounts into groups of 50 units and visualizing their distribution across different times of the day.

### 2. Time of Day Analysis
The `Time_of_Day` feature is used to categorize the time of transactions and analyze their frequency across different parts of the day.

#### Code Example
Here’s a snippet of the code used to visualize the distribution of transaction amounts:

```python
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd

bins = list(range(0, 2050, 50))

time_of_day_categories = fraud_df['Time_of_Day'].unique()
n_rows = len(time_of_day_categories) // 2 + len(time_of_day_categories) % 2
fig, axes = plt.subplots(nrows=n_rows, ncols=2, figsize=(14, 5 * n_rows), sharex=True, sharey=True)
axes = axes.flatten()

for i, time in enumerate(time_of_day_categories):
    ax = axes[i]
    
    time_df = fraud_df[fraud_df['Time_of_Day'] == time]
    
    sns.histplot(time_df['Amount'], bins=bins, ax=ax, color='blue', kde=False)
    ax.set_title(f'Amount Distribution for {time}')
    ax.set_xlabel('Amount')
    ax.set_ylabel('Frequency')

plt.tight_layout()
plt.show()
```

## Results
- The distribution of transaction amounts shows varying patterns across different times of the day.
- Fraudulent transactions tend to occur at specific times more frequently, and the amounts vary widely depending on the time.

## Conclusion
The analysis reveals distinct patterns in fraudulent transactions, particularly when considering the amount and time of day. These insights could potentially aid in developing more robust fraud detection models.

## Contributing
Contributions are welcome! If you have suggestions or improvements, please submit a pull request or open an issue.

## License
This project is licensed under the Samsung Innovation Campus (SIC) guidance.
```

