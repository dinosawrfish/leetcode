## Approach
Given an m x n matrix, I need to set the column and row elements to zero if that element is zero in place. Meaning I will have to calculate a way to identify all the indeces for that elements row and column.

I cannot scan the matrix and modify to zeros at the same time since I won't know which zeros were there originally or modified to.

I would need to scan the entire matrix first, recording the indices of elements with zeros.

Then I would go through the recorded indices, modifying the matrix at that row and column.

Given indices (x, y) in an m x n matrix, x being the row index and y being the col index:

to change all values in row x
- traverse matrix[x][0]...matrix[x][n] and change value to zero

to change all values in col y
- traverse matrix[0][y]...matrix[m][y] and change value to zero

## Code
``` python
def setZeroes(self, matrix: List[List[int]]) -> None:

        zero_elements = []

        num_rows = len(matrix)
        num_cols = len(matrix[0])

        for row_num in range(num_rows):
            for col_num in range(num_cols):
                if matrix[row_num][col_num] == 0:
                    zero_elements.append([row_num, col_num])

        for element in zero_elements:

            zero_col = element[1]
            zero_row = element[0]

            for row_num in range(num_rows):
                matrix[row_num][zero_col] = 0

            for col_num in range(num_cols):
                matrix[zero_row][col_num] = 0
```

## Time/Memory

Time Complexity: O(n*m) n and m being the number of rows and columns in the matrix. There are two nested for loops used to check every element in the matrix.

Space Complexity: O(n*m) since we are storing the indices in a list and worst case scenario, a given matrix has all its elements to zero so we would have to store that many indices.


## Approach 2
What if we want to reduce the space complexity? Essentially no new marker can be created to keep track of where zeros happen, so we can find a way to track the zeros within the matrix.

We can use the 0th row and column as the marker. We would need to find a way to know whether the 0th row and column will need to be modified.

- if there is a zero at the 0th row, we can place a marker at (0,0).
- if there is a zero at the 0th col, since (0,0) is already used as a marker for the row, we can track with a simple boolean variable.

## Code
``` python
def setZeroes(self, matrix: List[List[int]]) -> None:

        is_col = False
        num_rows = len(matrix)
        num_cols = len(matrix[0])

        for row in range(num_rows):

            if matrix[row][0] == 0:
                is_col = True

            for col in range(1, num_cols):
                if matrix[row][col] == 0:
                    matrix[0][col] = 0
                    matrix[row][0] = 0

        for row in range(1, num_rows):
            for col in range(1, num_cols):
                if matrix[row][0] == 0 or matrix[0][col] == 0:
                    matrix[row][col] = 0

        if matrix[0][0] == 0:
            for col in range(num_cols):
                matrix[0][col] = 0

        if is_col:
            for row in range(num_rows):
                matrix[row][0] = 0
```

## Time/Memory

Time Complexity: O(n*m) n and m being the number of rows and columns in the matrix. There are two nested for loops used to check every element in the matrix.

Space Complexity: O(1) The only variable created is a constant boolean.