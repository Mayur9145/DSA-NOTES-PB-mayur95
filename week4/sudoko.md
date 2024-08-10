# Sudoko solver problem from leetcode

[leetcode]()


```python
The given code solves a Sudoku puzzle using a backtracking algorithm. The solveSudoku method modifies the board in place to fill in the correct numbers.

Code Explanation


def solveSudoku(self, board: List[List[str]]) -> None:
This defines the solveSudoku method, which takes a 2D list board as input and returns nothing. The board is modified in place.

Solve Function


def solve(board):
The solve function is a recursive helper function used to try and solve the Sudoku board.

Finding Empty Cells


for i in range(len(board)):
    for j in range(len(board[0])):
        if board[i][j] == '.':
The nested loops iterate through each cell in the board to find empty cells (denoted by '.').

Trying Possible Values

for c in '123456789':
    if isValid(board, i, j, c):
        board[i][j] = c
For each empty cell, the code tries digits from '1' to '9'. The isValid function checks if placing the digit c in the current cell is valid.

Recursive Call and Backtracking


if(solve(board)):
    return True
else:
    board[i][j] = '.'
If placing the digit leads to a solution (solve(board) returns True), it returns True. If not, it resets the cell to '.' (backtracks) and tries the next digit.

Base Case


return True
If all cells are filled correctly, the function returns True.

Validity Check


def isValid(board, row, col, c):
    for i in range(9):
        if(board[i][col] == c):
            return False
        if(board[row][i] == c):
            return False
        if(board[3*(row//3)+i//3][3*(col//3)+i%3] == c):
            return False
    return True
The isValid function checks if placing digit c at board[row][col] violates Sudoku rules:

Checks the column for duplicates.
Checks the row for duplicates.
Checks the 3x3 subgrid for duplicates.
Initiate Solving


solve(board)
This line initiates the solving process by calling the solve function with the initial board.






```