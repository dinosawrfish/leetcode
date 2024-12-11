## Approach
I need to get the number of rows and columns in a dataframe in an array.

I think pandas has built in functions that will return that information of a dataframe

## Code

``` python
def getDataframeSize(players: pd.DataFrame) -> List[int]:
    size = players.shape
    return list(size)

```

## Runtime/Space Complexity