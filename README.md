# Real Estate Data Analysis - Lake View Properties
## Overview
### This project performs analysis on a dataset of real estate listings to identify properties with "lake view." Using natural language processing (NLP) techniques and regular expressions, it scans various fields such as PublicRemarks, WaterfrontFeatures, and View to determine whether a property has a "lake view." The goal is to process the raw dataset, clean it, and identify which properties have this desirable feature.
## Features
### Lake View Identification: The script checks for the presence of the phrase "lake view" or variations like "lake view from window" or "lake view in the north" in relevant text fields.
### Null Handling: Null values in the data are handled gracefully, ensuring the analysis does not break due to missing data.
### Flexible Data Sources: The script works with data in JSON format and converts it to a structured DataFrame for further analysis.
```python
import json
import pandas as pd

# Load json file
with open('listhub.json', 'r') as file:
    raw_data = file.readlines()  # Read each line

# Convert each line to a Dictionary 
json_data = [json.loads(line) for line in raw_data]

# Convert to a DataFrame 
df = pd.DataFrame(json_data)

df.head()
```
### 1.  Identify Nullable Fields:
### o  Find all the fields that are nullable.
### o  For those fields, calculate the total occurrences of null values.

## Find all columns with null values and their counts
```python
null_counts = df.isnull().sum()
nullable_fields = null_counts[null_counts > 0]  # Only columns with null values
print(nullable_fields)
```

## Display nullable fields and their null value counts

###  Identify 'Lake View' Properties: a)Use regular expressions to determine whether a property has a lake view. b)Search for mentions of "lake view" in the following fields: PublicRemarks WaterfrontFeatures[] View[]

### The re module in Python provides support for working with regular expressions (regex). A regular expression is a sequence of characters that defines a search pattern. Regular expressions are used for matching, searching, and manipulating strings in Python.

##  Identify 'Lake View' Properties:
### Use regular expressions to determine whether a property has a lake view.
### Search for mentions of "lake view" in the following fields:
### PublicRemarks
### WaterfrontFeatures[]
### View[]
 
