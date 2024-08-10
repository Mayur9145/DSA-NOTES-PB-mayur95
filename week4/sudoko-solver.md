

# SUDOKO SOLVER 


[leetcode]()


>TC=O(9^N),where N is the number of empty cells.

>SC=  O(N), where N is the number of empty cells (due to recursion depth).

```python

class Solution:
    def solveSudoku(self, board: List[List[str]]) -> None:
        """
        Do not return anything, modify board in-place instead.
        """
        def solve(board):
            for i in range(len(board)):
                for j in range(len(board[0])):
                    if board[i][j] == '.':
                        for c in '123456789':
                            if isValid(board, i, j, c):
                                board[i][j] = c

                                if(solve(board)):
                                    return True
                                else:
                                    board[i][j] = '.'
                        return False
            return True

        def isValid(board, row, col, c):
                for i in range(9):
                    if(board[i][col] == c):
                        return False
                    if(board[row][i] == c):
                        return False
                    if(board[3*(row//3)+i//3][3*(col//3)+i%3] == c):
                        return False
                return True

        solve(board)
            
            
        

```


## APPROACH

# Sudoku Solver Approach

## Approach

The Sudoku solver is implemented using a backtracking algorithm. Here's a step-by-step explanation of the approach:

1. **Backtracking Algorithm**:
    - The algorithm tries to fill in the empty cells with digits from `1` to `9`.
    - For each empty cell, we check if placing a digit is valid.
    - If valid, we place the digit and recursively attempt to solve the rest of the board.
    - If placing the digit does not lead to a solution, we backtrack by removing the digit and trying the next one.
    - This process continues until the board is completely and correctly filled.

2. **Validation**:
    - To ensure a digit can be placed in a cell, we check:
      - The digit is not already present in the same row.
      - The digit is not already present in the same column.
      - The digit is not already present in the 3x3 sub-grid that contains the cell.

## Example Walkthrough

Consider the following Sudoku board:





### Steps:

1. **Find an Empty Cell**:
   - Start with the first empty cell (row 0, column 2). The value is `.`.

2. **Try Digits 1 to 9**:
   - Check if placing each digit from `1` to `9` in the empty cell is valid using the `isValid` function.
   - For example, placing `1` in cell (0,2):
     - Not valid because `1` is already present in the first row.
   - Continue this process until a valid digit is found.

3. **Place Valid Digit**:
   - If placing `3` in cell (0,2) is valid:
     - Place `3` in (0,2) and proceed to solve the next empty cell.

4. **Recursive Backtracking**:
   - Repeat the process for the next empty cell. For each cell, try all digits and recursively fill the board.

5. **Backtrack if Necessary**:
   - If placing a digit does not lead to a solution, backtrack by removing the digit and trying the next one.

### Example Progression:

- Place `3` in cell (0,2):



- Continue filling in subsequent cells and backtracking as needed.

Finally, after all cells are correctly filled, the Sudoku board will be solved.

## Complexity

- **Time Complexity**: `O(9^N)`, where `N` is the number of empty cells.
- **Space Complexity**: `O(N)`, where `N` is the number of empty cells (due to recursion depth).





