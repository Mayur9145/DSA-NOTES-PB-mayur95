# Matrix Diagonal Sum

## Time Complexity-
## Space Complexity-             

[leetcode](https://leetcode.com/problems/matrix-diagonal-sum/description/)


>Approach


Problem Description:
Given a square matrix (n x n), we want to compute the sum of:
      
The main diagonal (elements from the top-left to bottom-right).
The anti-diagonal (elements from the top-right to bottom-left).
If the matrix has an odd size (n is odd), the middle element will be counted in both diagonals. So, we subtract this middle element once to avoid double-counting.
Step-by-Step Approach:
Input the Matrix:

First, we take a square matrix as input. In this example, we use a 3x3 matrix:
python

matrix = np.array([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
])
Determine the Size of the Matrix:

We assume that the matrix is square, so the number of rows and columns is the same (denoted as n).
python

n = len(matrix)  # n = 3 for this 3x3 matrix
Calculate the Sum of the Main Diagonal:

The main diagonal consists of elements where the row index equals the column index (i.e., matrix[i][i] for i ranging from 0 to n-1).
For our example matrix, the main diagonal elements are 1, 5, and 9.
python

main_diagonal_sum = sum(matrix[i][i] for i in range(n))  # 1 + 5 + 9 = 15
Calculate the Sum of the Anti-Diagonal:

The anti-diagonal consists of elements where the row index and column index add up to n-1 (i.e., matrix[i][n-1-i] for i ranging from 0 to n-1).
For our example matrix, the anti-diagonal elements are 3, 5, and 7.


anti_diagonal_sum = sum(matrix[i][n - 1 - i] for i in range(n))  # 3 + 5 + 7 = 15
Combine the Sums:

Add the sums of the main and anti-diagonals.


total_sum = main_diagonal_sum + anti_diagonal_sum  # 15 + 15 = 30
Adjust for the Middle Element (If Needed):

If the matrix has an odd size (which it does in this example, as n=3), the middle element (which lies on both diagonals) is subtracted once to avoid double-counting.
The middle element in a 3x3 matrix is at position [1][1], which is 5.
python

if n % 2 == 1:
    middle_index = n // 2
    total_sum -= matrix[middle_index][middle_index]  # 30 - 5 = 25
Return the Final Result:

The final sum, after the middle element adjustment, is returned.
python

return total_sum  # Returns 25








```python
import numpy as np

def sum_diagonals(matrix):
    n = len(matrix)  # Assuming matrix is square (n x n)
    
    main_diagonal_sum = sum(matrix[i][i] for i in range(n))
    anti_diagonal_sum = sum(matrix[i][n - 1 - i] for i in range(n))
    
    total_sum = main_diagonal_sum + anti_diagonal_sum
    
    # Subtract the middle element once if the matrix size is odd
    if n % 2 == 1:
        middle_index = n // 2
        total_sum -= matrix[middle_index][middle_index]
    
    return total_sum

# Example usage
matrix = np.array([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
])

result = sum_diagonals(matrix)
print("The sum of the main and anti-diagonal, subtracting the middle element once (if square matrix), is:", result)```



## Some logic breakdown



```python
anti_diagonal_sum = sum(matrix[i][n - 1 - i] for i in range(n))
```

is used to calculate the sum of the elements in the anti-diagonal (sometimes called the secondary diagonal) of a square matrix.

### Breakdown of the Code:

1. **`matrix[i][n - 1 - i]`**:
   - Here, `i` is the row index (ranging from 0 to `n-1`).
   - `n` is the size of the matrix (i.e., the number of rows or columns).
   - `n - 1 - i` is the column index that corresponds to the anti-diagonal element in the `i`th row.
   
   The key idea is that for the anti-diagonal, the column index decreases as the row index increases:
   - When `i = 0` (first row), the column index is `n - 1 - 0 = n - 1` (last column).
   - When `i = 1` (second row), the column index is `n - 1 - 1 = n - 2` (second last column).
   - And so on, until:
   - When `i = n - 1` (last row), the column index is `n - 1 - (n - 1) = 0` (first column).

   This pattern effectively selects elements along the anti-diagonal.

2. **`for i in range(n)`**:
   - This part of the code creates a loop that iterates over all the rows of the matrix, from `0` to `n-1`.

3. **`sum(...)`**:
   - The `sum` function adds up all the elements selected by the expression `matrix[i][n - 1 - i]` for each `i`.

### Example:

Consider a 3x3 matrix:

```
1 2 3
4 5 6
7 8 9
```

Let's apply the line of code:

- For `i = 0`: `matrix[0][3-1-0] = matrix[0][2] = 3`
- For `i = 1`: `matrix[1][3-1-1] = matrix[1][1] = 5`
- For `i = 2`: `matrix[2][3-1-2] = matrix[2][0] = 7`

So, the anti-diagonal elements are `3`, `5`, and `7`. The sum of these elements is:

```
3 + 5 + 7 = 15
```

Thus, `anti_diagonal_sum` would be `15` for this 3x3 matrix.
