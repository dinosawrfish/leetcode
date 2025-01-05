## Approach
Given an n x n matrix with each  element containing a value, I need to find the sum of the diagonals. Values from the second diagonal should not be included if it was part of the primary diagonal.

I need to identify what is a diagonal.

For a 3x3 matrix
The indexes in the primary diagonal are
(0, 0), (1, 1), (2, 2)
or when row  index == col index
secondary diagonal are
(0, 2), (1, 1), (2, 0)
or when row index + col index = 2 = 3 - 1 = n - 1 (n being number of rows in square matrix)

We can go through the matrix and add values when the indexes meet the conditions of row_ind == col_ind or row_ind + col_ind = n - 1.

## Code
``` python
    def diagonalSum(self, mat: List[List[int]]) -> int:

        sum = 0
        num_rows = len(mat)

        for ind in range(num_rows):
            sum += mat[ind][ind]
            sum += mat[ind][num_rows - 1 - ind]

        if num_rows % 2 != 0:
            sum -= mat[num_rows // 2][num_rows // 2]

        return sum
```

## Runtime/Memory
Time Complexity: O(n) n being the number of rows and cols in the matrix

Space Complexity: O(1) Constant space since we are only keeping track of numeric values.