


# Finding island problem from github

[leetcode](https://leetcode.com/problems/number-of-islands/submissions/1375916429/)



### Time Complexity
The time complexity of the `numIslands` function is **O(M * N)**, where `M` is the number of rows and `N` is the number of columns in the grid. This is because the algorithm iterates through each cell of the grid, and for each cell that is part of an island (`'1'`), it performs a depth-first search (DFS) to visit all connected land cells. Each cell is visited exactly once, so the overall time complexity is linear with respect to the number of cells in the grid.

### Space Complexity
The space complexity of the `numIslands` function is **O(M * N)** in the worst case due to the recursive stack space used by the DFS. In the worst-case scenario, where the grid is entirely land (`'1'`), the recursion might go as deep as the total number of cells in the grid, which would be `M * N`. Therefore, the space complexity is also linear with respect to the number of cells in the grid.




```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        if not grid:
            return 0

        def dfs(i, j):
            if i < 0 or i >= len(grid) or j < 0 or j >= len(grid[0]) or grid[i][j] == '0':
                return

            grid[i][j] = '0'

            dfs(i - 1, j)  # Up
            dfs(i + 1, j)  # Down
            dfs(i, j - 1)  # Left
            dfs(i, j + 1)  # Right

        count = 0
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                if grid[i][j] == '1':  # Found an island
                    dfs(i, j)  # Start DFS to mark the whole island
                    count += 1  # Increase the count for each island

        return count

 

```

# Number of Islands Problem - DFS Approach

## Problem Statement

Given a 2D grid of `'1'`s (land) and `'0'`s (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are surrounded by water.

## Approach

We can solve this problem using Depth-First Search (DFS). The idea is to traverse each cell of the grid. When we encounter a `'1'`, it means we've found a new island. We then use DFS to visit all the adjacent `'1'`s and mark them as `'0'` to indicate that they have been visited and are part of the current island. The count of islands is incremented each time a new `'1'` is found.

### Step-by-Step Explanation

1. **Initialization**:
    - Check if the grid is empty; if it is, return `0` as there are no islands.
    - Define a nested DFS function that will traverse the grid and mark the connected `'1'`s as `'0'`.

2. **DFS Function**:
    - The DFS function checks boundary conditions and whether the current cell is water (`'0'`). If so, it returns immediately.
    - If the cell is land (`'1'`), it marks it as visited by setting it to `'0'`.
    - The DFS function then recursively calls itself to visit the adjacent cells (up, down, left, right).

3. **Counting Islands**:
    - Iterate over each cell in the grid. If a cell contains `'1'`, it indicates a new island.
    - Call the DFS function to mark the entire island.
    - Increase the island count.

4. **Return the Result**:
    - After traversing the entire grid, return the total count of islands.







