## Approach
Given a dataframe, display the first three rows.

I need to find a property or built in function in df that lets me specify the amount of rows to return.

There are multiple ways to accomplish this.
- can slice through the dataframe directly `df[:3]`
- using the loc function `df.loc[:2]` this is not ideal if indexes are not sorted
- using iloc function selects by position `df.iloc[:3]`
- using head function `df.head(3)`

## Code

``` python
def selectFirstRows(employees: pd.DataFrame) -> pd.DataFrame:
    return employees.head(3)
```

## Time/Space Complexity