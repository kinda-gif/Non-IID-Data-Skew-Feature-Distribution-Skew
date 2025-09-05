# Feature Splitter

A Python library for splitting datasets into sub-datasets based on Feature Distribution Skew, using the column with the highest value differentiation. Offers tools for skew analysis, visualization, and preprocessing. Compatible with Pandas, NumPy, and Scikit-learn.

## Installation

To install the `feature_splitter` library, you can use pip:

```bash
pip install pandas
pip install feature-splitter
```

Note: This library requires `pandas` to be installed.

## Usage

The `feature_splitter` library provides a simple function to split a Pandas DataFrame into multiple parts based on the variance of its columns. This can be useful for creating balanced datasets for A/B testing or other analytical purposes.

### Example

```python
import pandas as pd
from feature_splitter.splitter import split_df_by_variation

# Create a sample DataFrame
data = {
    'col1': [10, 20, 30, 40, 50, 60, 70, 80, 90, 100],
    'col2': [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
    'col3': [100, 90, 80, 70, 60, 50, 40, 30, 20, 10]
}
df = pd.DataFrame(data)

# Split the DataFrame into 2 parts
splitted_dfs = split_df_by_variation(df, n_splits=2, prefix='output_part')

# You can now work with the split DataFrames
for i, part_df in enumerate(splitted_dfs):
    print(f'\nDataFrame part {i+1}:')
    print(part_df)

# The function also saves each split as a CSV file (e.g., output_part1.csv, output_part2.csv)
```

## Function Reference

### `split_df_by_variation(df, n_splits=4, prefix='Client')`

Splits a DataFrame into `n_splits` parts based on sorting by the column with the highest variance. Saves each split as a CSV file with filenames like `{prefix}1.csv`, `{prefix}2.csv`, etc.

**Parameters:**

- `df` (pd.DataFrame): Input DataFrame.
- `n_splits` (int, optional): Number of parts to split into. Defaults to 4.
- `prefix` (str, optional): Prefix for the output CSV files. Defaults to 'Client'.

**Returns:**

- `list of pd.DataFrame`: List of split DataFrames.

## License



This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

