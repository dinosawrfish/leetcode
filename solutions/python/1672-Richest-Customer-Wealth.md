## Approach

To get the customer with the max amount of money, my initial thought at the time was to iterate through the grid and get the sum of each customer then return the customer with the max amount of money.

## Code

``` python

class Solution:
    def maximumWealth(self, accounts: List[List[int]]) -> int:
        for i in range(len(accounts)):
            accounts[i] = sum(accounts[i])
        return max(accounts)

```

## Runtime/Memory

Runtime: O(n * m) n being the length of the integer grid since the function iterates per row in the grid. Per row i n, the sum is calculated which takes O(m) m being the number of columns within the row.

Memory: O(1) since the given grid is being manipulated