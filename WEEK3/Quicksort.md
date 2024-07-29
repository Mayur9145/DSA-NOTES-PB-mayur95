```python
## function definition of partition
def partition(arr, p, q):
  pivot = arr[p]
  i = p
  for j in range(i+1, q+1):
    if arr[j] <= pivot:
      i = i + 1
      ## swap arr[i] with arr[j]
      arr[i], arr[j] = arr[j], arr[i]
  ## final swap between arr[i] and pivot
  arr[i], arr[p] = arr[p], arr[i]
  return i

## function definition of quicksort
def quickSort(arr, p, q):
  if p < q:
    ## 1. Divide
    mid = partition(arr, p, q)
    ## 2. Conquer
    ## recursively call the left subtree
    quickSort(arr, p, mid-1)
    ## recursively call the right subtree
    quickSort(arr, mid+1, q)
  return arr

## Driver code
arr = [50, 20, 45, 11, 15, 27, 34]
p = 0
q = len(arr) - 1
## function calling
result = quickSort(arr, p, q)
print(result)
```

>APPROACH



### 1. **Partition Function**

The `partition` function is responsible for arranging the elements around a pivot element so that all elements less than or equal to the pivot are on its left and all elements greater than the pivot are on its right.

- **Input**: `arr` (the list to be sorted), `p` (the starting index), and `q` (the ending index).
- **Pivot Selection**: The pivot is selected as the element at index `p` (the starting index of the current subarray).
- **Rearranging Elements**:
  - Initialize `i` to `p` (the starting index).
  - Traverse through the subarray from index `p+1` to `q`. For each element `arr[j]`, if it is less than or equal to the pivot, increment `i` and swap `arr[i]` with `arr[j]`.
- **Final Swap**: After traversing the subarray, swap the pivot element `arr[p]` with the element `arr[i]` so that the pivot is placed in its correct position.
- **Return**: Return the index `i`, which is the final position of the pivot.

### 2. **QuickSort Function**

The `quickSort` function recursively sorts the array using the partition function.

- **Input**: `arr` (the list to be sorted), `p` (the starting index), and `q` (the ending index).
- **Base Case**: If `p` is less than `q`, the subarray needs sorting. If `p` is not less than `q`, the subarray is already sorted or empty.
- **Divide**: Call the `partition` function to rearrange the elements around a pivot. This function returns the pivot's final position `mid`.
- **Conquer**: Recursively apply `quickSort` on the left and right subarrays:
  - The left subarray is from `p` to `mid-1`.
  - The right subarray is from `mid+1` to `q`.
- **Return**: After sorting, return the sorted array.

### 3. **Driver Code**

- Define an array `arr` to be sorted.
- Set the starting index `p` to `0` and the ending index `q` to `len(arr) - 1`.
- Call the `quickSort` function with the array and indices.
- Print the sorted array.

### Summary of Steps

1. **Partition**: Choose a pivot, rearrange elements, and return the pivot’s position.
2. **QuickSort**: Recursively sort the left and right subarrays around the pivot.
3. **Driver Code**: Initialize the array and call `quickSort` to sort and print the result.

### This approach efficiently sorts the array by breaking it down into smaller subarrays and sorting those. The efficiency comes from the fact that QuickSort typically has an average time complexity of O(n log n), though it can degrade to O(n^2) in the worst case (e.g., when the array is already sorted).




