# Diameter of a binary tree



[leetcode](https://leetcode.com/problems/diameter-of-binary-tree/submissions/1359063996/)



**Time Complexity: O(n)**

- Each node is visited exactly once during the traversal of the tree. Therefore, the time complexity is linear with respect to the number of nodes in the tree.

**Space Complexity: O(h)**

- The space complexity is determined by the maximum height of the recursion stack. In the worst case (a skewed tree), this is O(n). However, for a balanced tree, it is O(log n), where n is the number of nodes.





```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def __init__(self):
        self.diameter = 0 

    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if root is None:
            return 0
        else:
            lheight = self.maxDepth(root.left)
            rheight = self.maxDepth(root.right)
            self.diameter = max(self.diameter, lheight + rheight)
            
        return max(lheight, rheight) + 1

    def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        self.maxDepth(root)  
        return self.diameter
```


 ## Approach to Find the Diameter of a Binary Tree

1. **Define the TreeNode class**:
   - Create a class `TreeNode` to represent each node in the binary tree with attributes for value (`val`), left child (`left`), and right child (`right`).

2. **Define the Solution class**:
   - Create a class `Solution` with the following methods:
   
   1. **`__init__` method**:
      - Initialize an instance variable `diameter` to keep track of the maximum diameter found during traversal.

   2. **`maxDepth` method**:
      - **Input**: A `TreeNode` object (`root`).
      - **Output**: The maximum depth of the subtree rooted at `root`.
      - **Logic**:
        - If the `root` is `None`, return `0` (base case for recursion).
        - Recursively find the maximum depth of the left and right subtrees.
        - Update the `diameter` as the maximum of the current `diameter` and the sum of the depths of the left and right subtrees.
        - Return the maximum depth of the subtree rooted at `root` plus `1` (accounting for the current node).

   3. **`diameterOfBinaryTree` method**:
      - **Input**: A `TreeNode` object (`root`).
      - **Output**: The diameter of the binary tree.
      - **Logic**:
        - Call the `maxDepth` method to compute the diameter.
        - Return the computed diameter.

3. **Explanation**:
   - The diameter of the binary tree is the length of the longest path between any two nodes in the tree. This path can pass through the root or not.
   - The `maxDepth` method computes the depth of each subtree and updates the diameter based on the longest path through the current node.
   - The `diameterOfBinaryTree` method initializes the process and returns the final diameter.

### Explanation of `maxDepth` Function

Sure! Here’s the entire explanation in one markdown block:

```markdown
### Explanation of `maxDepth` Function

The `maxDepth` function is a recursive method used to compute the maximum depth of a binary tree while also updating the diameter of the tree. Here's a step-by-step breakdown:

1. **Base Case**:
   ```python
   if root is None:
       return 0
   ```
   If the current node (`root`) is `None`, it means we've reached the end of a branch, so the depth is `0`.

2. **Recursive Case**:
   ```python
   lheight = self.maxDepth(root.left)
   rheight = self.maxDepth(root.right)
   ```
   Recursively compute the maximum depth of the left subtree (`lheight`) and the right subtree (`rheight`).

3. **Update Diameter**:
   ```python
   self.diameter = max(self.diameter, lheight + rheight)
   ```
   The diameter of the tree is updated to be the maximum of its current value or the sum of the depths of the left and right subtrees. This is because the diameter of the tree can be defined as the longest path between any two nodes in the tree, which can be through the root.

4. **Return Depth**:
   ```python
   return max(lheight, rheight) + 1
   ```
   The function returns the maximum depth of the tree rooted at the current node. The depth is computed as the maximum of the depths of the left and right subtrees plus one (for the current node itself).

In summary, `maxDepth` computes the depth of the current subtree and simultaneously updates the diameter of the tree based on the sum of the depths of its left and right subtrees.
```