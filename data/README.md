Due to the file size limitation of GitHub (a maximum of 100MB per file), we need to split a large dataset into multiple smaller CSV files. This article will introduce how to use Python scripts to split and merge datasets.
```python
import pandas as pd
import glob

# Get all split CSV files
csv_files = glob.glob("data_*.csv")

# Initialize an empty list to store data
df_list = []


for file in csv_files:
    df_chunk = pd.read_csv(file)
    df_list.append(df_chunk)

# Merge all DataFrames into one DataFrame
df_combined = pd.concat(df_list, ignore_index=True)

# Save the merged DataFrame
df_combined.to_csv('combined_data.csv', index=False)

print("All files have been merged successfully.")
```

