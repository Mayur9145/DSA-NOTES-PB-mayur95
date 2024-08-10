## TWO SUM USING LINKEDLIST RECURSION




[leetcode](https://leetcode.com/problems/add-two-numbers/)



# Approach: Add Two Numbers Represented by Linked Lists

## Problem Statement
Given two non-empty linked lists representing two non-negative integers, add the two numbers and return the sum as a linked list. The digits are stored in reverse order, and each of their nodes contains a single digit. You may assume the two numbers do not contain any leading zero, except the number 0 itself.

## Approach

1. **Initialization**:
   - Start by initializing a dummy node to help in easily building the result list.
   - Use two pointers, `l1` and `l2`, to traverse the input linked lists.
   - Initialize a variable `carry` to handle sums greater than or equal to 10.

2. **Traverse Both Lists**:
   - Loop through the linked lists until both `l1` and `l2` are `None` and `carry` is 0.
   - For each node:
     - Retrieve the value of the current node from `l1` and `l2` (use 0 if a list is exhausted).
     - Calculate the sum of these values and the current `carry`.
     - Determine the new value (`value`) of the current digit as `total % 10`.
     - Update the `carry` as `total // 10`.
     - Create a new node with `value` and attach it to the result list.
     - Move to the next nodes in `l1` and `l2`.

3. **Handle Remaining Carry**:
   - After the loop, if there's still a carry, add a new node with the carry value.

4. **Return Result**:
   - Return the `next` of the dummy node, which is the head of the resultant linked list.

## Example Walkthrough

Let's walk through an example:

**Input**:  
`l1`: 2 -> 4 -> 3  
`l2`: 5 -> 6 -> 4  

These represent the numbers 342 and 465.

### Step-by-Step Calculation

| Step | l1  | l2  | Carry | Sum (l1 + l2 + Carry) | Result Digit | New Carry |
|------|-----|-----|-------|-----------------------|--------------|-----------|
| 1    | 2   | 5   | 0     | 7 (2 + 5 + 0)         | 7            | 0         |
| 2    | 4   | 6   | 0     | 10 (4 + 6 + 0)        | 0            | 1         |
| 3    | 3   | 4   | 1     | 8 (3 + 4 + 1)         | 8            | 0         |

**Output**:  
The resultant linked list is `7 -> 0 -> 8`, representing the number 807.



```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode, carry=0) -> ListNode:
        if not l1 and not l2 and carry == 0:
            return None
        
        val1 = l1.val if l1 else 0
        val2 = l2.val if l2 else 0
        total = val1 + val2 + carry
        carry = total // 10
        value = total % 10
        
        result_node = ListNode(value)
        
        next_l1 = l1.next if l1 else None
        next_l2 = l2.next if l2 else None
        result_node.next = self.addTwoNumbers(next_l1, next_l2, carry)
        
        return result_node



## Explanation

- **Result**: The sum of the two input numbers is calculated digit by digit and is stored in a new linked list.
- **Carry Handling**: If the sum of two digits exceeds 9, the carry is passed to the next digit.
- **Edge Cases**: Handles cases where the linked lists are of different lengths and cases where a final carry needs to be added as a new node.

## Complexity Analysis

- **Time Complexity**: O(max(m, n)), where `m` and `n` are the lengths of the input lists `l1` and `l2`, respectively. The function processes each node in both lists once.
- **Space Complexity**: O(max(m, n)) for storing the result list, where each node in the resulting linked list is created for each sum operation.












# code implementation
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode, carry=0) -> ListNode:
        # Base case: if both lists are empty and no carry, return None
        if not l1 and not l2 and carry == 0:
            return None
        
        # Calculate the value and carry
        val1 = l1.val if l1 else 0
        val2 = l2.val if l2 else 0
        total = val1 + val2 + carry
        carry = total // 10
        value = total % 10
        
        # Create a new node with the calculated value
        result_node = ListNode(value)
        
        # Recurse with the next nodes of l1 and l2
        next_l1 = l1.next if l1 else None
        next_l2 = l2.next if l2 else None
        result_node.next = self.addTwoNumbers(next_l1, next_l2, carry)
        
        return result_node

# Helper function to print the linked list
        def print_list(node):
            while node:
                print(node.val, end=" -> ")
                node = next_node
        print("None")

# Example Usage:
# Create linked lists 2 -> 4 -> 3 and 5 -> 6 -> 4
        l1 = ListNode(2, ListNode(4, ListNode(3)))
        l2 = ListNode(5, ListNode(6, ListNode(4)))

# Solution instance
        solution = Solution()
        result = solution.addTwoNumbers(l1, l2)

# Print the result
        print_list(result)









```


