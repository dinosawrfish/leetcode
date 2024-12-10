## Approach

Create a DataFrame from a 2D list of data `student_data`.

student_data:
`[
  [1, 15],
  [2, 11],
  [3, 11],
  [4, 20]
]`

I need to keep the same order of data, and the df should have two columns `student_id` and `age`.

The goal is essentially to create a df from an array. To do that I can call `DataFrame` from `pd` and set data to `student_data` and set columns in an array with the desired column names.

## Code

``` python
import pandas as pd

def createDataframe(student_data: List[List[int]]) -> pd.DataFrame:
    df = pd.DataFrame(data=student_data, columns=['student_id', 'age'])
```

## Runtime/Memory

Runtime: O(n) n being the number of rows in `student_data`
Memory: O(n) n being the number of rows in `student_data` since df will store all rows.