## Approach
I need to return a row of a df given a column name and its value.

I can locate a row using label selection and return only the specified columns.
`df.loc[df['id'] == 123]`
I need to also specify what columns to return
`df.loc[df['id'] == 123, ['col1', 'col2']]`
## Code
``` python
import pandas as pd

def selectData(students: pd.DataFrame) -> pd.DataFrame:
    selected_student = students.loc[students['student_id'] == 101, ['name', 'age']]
    return selected_student
```

## Time/Space Complexity