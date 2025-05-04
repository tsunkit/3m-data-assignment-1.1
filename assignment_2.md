# Assignment 1

## Instructions

Paste the answer to each question in the answer code section below each question.

### Question 1

Given the following numpy array:

```python
arr = np.array([1, 2, 3, 4, 5])
```

Write a Python code to multiply each element in the array by 2.

Answer:

```python

```

### Question 2

Given the following 2D numpy array:

```python
arr = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
```

Write a Python code to select the second row of the array.

Answer:

```python

```
### Question 3

Given the following 2D numpy array:

```python
arr = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
```

Write a Python code to calculate the average of all the elements.

Answer:

```python

```
### Question 4

Question: Select all numeric columns except float from the DataFrame `dft`.

Answer:

```python

```

### Question 5

Question: How do you return the last 3 rows of a DataFrame `df`?

Answer:

```python

```

### Question 6

Question: Return the minimum and maximum of a Series `x` as a new Series with the index `["min", "max"]`.

Answer:

```python

```

### Question 7

Question: How do you select rows from a DataFrame where any value in the row exceeds a threshold?

```python
import pandas as pd

df = pd.DataFrame({'A': [1, 2, 3, 4, 5], 'B': [10, 20, 30, 40, 50]})
threshold = 30
```

Answer:

```python

```

### Question 8

Question: How do you compute the cumulative sum of a column in a DataFrame?

```python
import pandas as pd

df = pd.DataFrame({'A': [1, 2, 3, 4, 5]})
```

Answer:

```python

```

### Question 9

Question: How do you convert a Series of strings to uppercase?

```python
import pandas as pd

series = pd.Series(['apple', 'banana', 'cherry'])
```

Answer:

```python

```

### Question 10

Question: Calculate the correlation between 'MSFT' and 'IBM' returns from a DataFrame of stock returns.

```python
import pandas as pd

# Assuming 'returns' is a DataFrame containing stock returns
returns = pd.DataFrame({
    'MSFT': [0.05, 0.07, -0.01],
    'IBM': [0.04, 0.02, 0.03]
})
```

Answer:

```python

```

### Question 11

Question: Slice the Series to return data from 5th to 15th January.

```python
import pandas as pd
import numpy as np

dates = pd.date_range("2023-01-01", "2023-01-31")
data = pd.Series(np.random.rand(len(dates)), index=dates)
```

Answer:

```python

```

### Question 12

Question: How to plot a histogram with 30 bins for `data` in matplotlib? Label the x and y axis as `X` and `Y` respectively.

```python
data = np.random.randn(1000)
```

Answer:

```python

```

### Question 13

Question: How do you create a bar plot in seaborn using the `tips` dataset to show the average tip amount per day?

```python
import seaborn as sns
tips = sns.load_dataset('tips')
```

Answer:

```python

```

### Question 14

Question: How to create a box plot for total_bill categorized by day in the `tips` dataset using seaborn?

Answer:

```python

```

## Submission

- Submit the GitHub URL of your assignment to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
