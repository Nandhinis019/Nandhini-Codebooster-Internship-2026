# Python Pandas & GitHub Notes

---

# 1. Pandas Basics

## Import Pandas Library

```python id="q7m2x1"
import pandas as pd
```

Pandas is used for:

* Reading datasets
* Cleaning data
* Analyzing data
* Performing operations on tables

---

# 2. Load CSV File

```python id="x4v8m2"
df = pd.read_csv('filename.csv')
```

* `read_csv()` loads CSV files into a DataFrame.
* `df` stands for DataFrame.

---

# 3. Display Data

## First 5 Rows

```python id="w2n5q8"
df.head()
```

## First 10 Rows

```python id="m9x1v4"
df.head(10)
```

## Last 5 Rows

```python id="t6k3p7"
df.tail()
```

---

# 4. Shape of Dataset

```python id="r5x2m8"
df.shape
```

### Output Format

```python id="y8q1n6"
(rows, columns)
```

Example:

```python id="v4m7x1"
(100, 13)
```

* `100` → Number of rows
* `13` → Number of columns

---

# 5. Data Types

```python id="z3n6k2"
df.dtypes
```

Shows the datatype of each column.

Examples:

* `int64`
* `float64`
* `object` (text/string)

---

# 6. Statistical Summary

```python id="c7m1x5"
df.describe()
```

Displays:

* Mean
* Count
* Minimum
* Maximum
* Standard Deviation

---

# 7. Missing Values

## Count Null Values

```python id="n5x8q3"
df.isnull().sum()
```

## Replace Null Values

```python id="k2v7m1"
df["semester"] = df["semester"].fillna(5)
```

---

# 8. Column Names

```python id="q1m8x4"
df.columns.tolist()
```

Converts all column names into a Python list.

---

# 9. Selecting Columns

## Single Column

```python id="x8n2v5"
df['column_name']
```

Example:

```python id="m4q7x1"
df['department']
```

---

# 10. Boolean Filtering

## Equal To

```python id="j5x1m8"
df[df['column'] == 'value']
```

Example:

```python id="r2n7v4"
df[df['city'] == 'Chennai']
```

---

## Greater Than

```python id="c8m2x6"
df[df['column'] > 80]
```

Example:

```python id="p1v5n9"
df[df['math_score'] > 80]
```

---

## Less Than

```python id="t7q3m1"
df[df['column'] < 75]
```

---

# 11. Using loc

`loc` means **location-based indexing**.

## Syntax

```python id="x3m8q1"
df.loc[row_condition, column_name]
```

## Example

```python id="n9v2x5"
df.loc[df['city'] == 'Chennai']
```

---

# 12. Multiple Conditions

```python id="p4m7x2"
df.loc[
    (df['city'] == 'Chennai') |
    (df['city'] == 'Mumbai')
]
```

---

# 13. GroupBy and Aggregation

## Average Per Group

```python id="w8x1m4"
df.groupby('column')['other'].mean()
```

Example:

```python id="k5q2v7"
df.groupby('department')['math_score'].mean()
```

---

## Value Counts

```python id="m1x9q3"
df['column'].value_counts()
```

Example:

```python id="v6n2x8"
df['department'].value_counts()
```

---

# 14. Sorting Data

## Highest First

```python id="q7x3m5"
df.sort_values(by='column', ascending=False)
```

## Lowest First

```python id="r2m8x1"
df.sort_values(by='column', ascending=True)
```

---

# 15. Creating New Columns

```python id="x5q1m7"
df['new_col'] = df['col1'] + df['col2']
```

Example:

```python id="k8m3x2"
df['total_score'] = (
    df['math_score'] +
    df['science_score'] +
    df['english_score'] +
    df['programming_score']
)
```

---

# 16. Top Performing Student

```python id="n4x7q2"
top_student = df.loc[df['total_score'].idxmax()]

display(top_student[['name', 'department', 'total_score']])
```

---

# 17. Lowest Performing Student

```python id="m2q8x5"
low_student = df.loc[df['total_score'].idxmin()]

display(low_student[['name', 'department', 'total_score']])
```

---

# 18. Save DataFrame

```python id="x1m5q9"
df.to_csv('output.csv', index=False)
```

* Saves DataFrame as CSV file
* `index=False` removes row numbers

---

# Types of Data

## Structured Data

* Organized in rows and columns
* Same format for every record
* Easy to store in databases

### Examples

* Student marksheet
* Attendance register
* Bank transactions

### Formats

* CSV
* Excel
* SQL

---

## Semi-Structured Data

* Has tags/labels
* Not fixed rows and columns
* Supports nested data

### Examples

* API responses
* WhatsApp metadata
* Config files

### Formats

* JSON
* XML

---

## Unstructured Data

* No predefined structure
* Difficult to store in tables directly

### Examples

* Images
* Videos
* Audio files
* PDFs

### Formats

* JPG
* MP4
* MP3
* PDF

---

## Important Fact

```text id="v8q2m1"
80% of data in the world is unstructured data.
```

---

# GitHub Key Concepts

| Term       | Meaning                  | Analogy             |
| ---------- | ------------------------ | ------------------- |
| Repository | Project folder on GitHub | Google Drive folder |
| Commit     | Save snapshot            | Ctrl + S            |
| Push       | Upload code              | Upload to Drive     |
| Pull       | Download code            | Download from Drive |
| README.md  | Project description      | Cover page          |
| Branch     | Separate version         | Experimental copy   |

---

# GitHub Setup Steps

1. Go to GitHub
2. Sign Up
3. Verify Email
4. Click `+`
5. Select `New Repository`
6. Repository Name:

   ```text id="7m4x1q"
   codeboosters-internship-2024
   ```
7. Set Repository to Public
8. Add README File
9. Click Create Repository

---

# Upload Notebook to GitHub

1. Open Repository
2. Click `Add File`
3. Select `Upload Files`
4. Upload `.ipynb` file
5. Add Commit Message
6. Click `Commit Changes`

---

# Common Errors and Fixes

| Error               | Solution                              |
| ------------------- | ------------------------------------- |
| ModuleNotFoundError | Install pandas using pip              |
| FileNotFoundError   | Upload CSV file correctly             |
| KeyError            | Check column names using `df.columns` |
| SyntaxError         | Check brackets and quotes             |
| IndentationError    | Use proper spacing                    |

---

# Dataset Reference — student_performance.csv

| Column                | Description           |
| --------------------- | --------------------- |
| student_id            | Unique student ID     |
| name                  | Student name          |
| age                   | Student age           |
| gender                | Male/Female           |
| department            | Department name       |
| semester              | Current semester      |
| math_score            | Math marks            |
| science_score         | Science marks         |
| english_score         | English marks         |
| programming_score     | Programming marks     |
| attendance_percentage | Attendance percentage |
| city                  | Student city          |
| admission_year        | Admission year        |

---

# Important Note

```text id="2q7m5x"
This dataset will be used across all internship days for practice and analysis.
```
