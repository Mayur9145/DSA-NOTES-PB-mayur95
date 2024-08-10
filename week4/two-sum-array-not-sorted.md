





# Two Sum (Unsorted Array) - Constant Space Complexity

This Python function solves the "Two Sum" problem for an unsorted array using a two-pointer technique with constant extra space complexity.

## Problem Statement

Given an unsorted array `arr` of integers and a target integer `target`, find the indices of the two numbers such that they add up to the target.

## Solution

### Approach

The solution follows these steps:

1. **Array with Indices**: 
   - Create a list of tuples where each tuple contains an element and its original index from the array.
   - This helps us to keep track of the original indices after sorting.

2. **Sorting**: 
   - Sort the list of tuples based on the array values (not indices).

3. **Two-Pointer Technique**:
   - Use two pointers (`left` and `right`) to iterate over the sorted list.
   - If the sum of the elements at the `left` and `right` pointers equals the target, return their original indices.
   - Adjust the pointers based on whether the sum is less than or greater than the target.

4. **Return**:
   - If a pair is found, return their original indices.
   - If no such pair exists, return `None`.

### Python Code

```python
def two_sum_unsorted(arr, target):
    # Create a list of tuples where each tuple contains an element and its original index
    arr_with_indices = [(value, index) for index, value in enumerate(arr)]
    
    # Sort the list by the array values
    arr_with_indices.sort(key=lambda x: x[0])
    
    # Initialize two pointers
    left, right = 0, len(arr_with_indices) - 1
    
    # Iterate while the left pointer is less than the right pointer
    while left < right:
        # Calculate the current sum
        current_sum = arr_with_indices[left][0] + arr_with_indices[right][0]
        
        # If the current sum matches the target, return the original indices
        if current_sum == target:
            return arr_with_indices[left][1], arr_with_indices[right][1]
        # If the current sum is less than the target, move the left pointer to the right
        elif current_sum < target:
            left += 1
        # If the current sum is greater than the target, move the right pointer to the left
        else:
            right -= 1
    
    # If no solution is found, return None
    return None






```python
def two_sum_unsorted(arr, target):
    # Create a list of tuples where each tuple contains an element and its original index
    arr_with_indices = [(value, index) for index, value in enumerate(arr)]
    
    # Sort the list by the array values
    arr_with_indices.sort(key=lambda x: x[0])
    
    # Initialize two pointers
    left, right = 0, len(arr_with_indices) - 1
    
    # Iterate while the left pointer is less than the right pointer
    while left < right:
        # Calculate the current sum
        current_sum = arr_with_indices[left][0] + arr_with_indices[right][0]
        
        # If the current sum matches the target, return the original indices
        if current_sum == target:
            return arr_with_indices[left][1], arr_with_indices[right][1]
        # If the current sum is less than the target, move the left pointer to the right
        elif current_sum < target:
            left += 1
        # If the current sum is greater than the target, move the right pointer to the left
        else:
            right -= 1
    
    # If no solution is found, return None
    return None

# Example usage:
arr = [3, 2, 4, 6, 5]
target = 10
result = two_sum_unsorted(arr, target)
print("Indices:", result)  # Output: Indices: (2, 4)


```

### Time Complexity

1. **Creating the list of tuples**: This step involves iterating over the array `arr` once to create `arr_with_indices`, which takes \(O(n)\) time, where \(n\) is the length of `arr`.
   
2. **Sorting the list**: The `arr_with_indices` list is sorted using Python’s Timsort algorithm, which has a time complexity of \(O(n \log n)\).

3. **Two-pointer traversal**: The two-pointer technique iterates through the list at most once, taking \(O(n)\) time.

Overall, the dominant term is the sorting step. Hence, the total time complexity is:
\[ O(n \log n) \]

### Space Complexity

1. **Storage for tuples**: The space required to store the tuples `(value, index)` is \(O(n)\), as there are `n` elements in `arr`.

2. **Other variables**: The extra space used by variables (e.g., `left`, `right`, `current_sum`) is constant, i.e., \(O(1)\).

Thus, the overall space complexity is:
\[ O(n) \]
