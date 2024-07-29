# MERGE SORT

[leetcode]()



## recurrence relation:
## T(n) = 2T(n/2) + n = O(nlogn)
## Space Complexity = O(n)
## function definition of mergeProcedure
## complexity of combine - n
```python
def mergeProcedure(arr, start, mid, end):
  ## create and initialize the left and right sorted subarray
  ## extra space - outplace sorting algorithm
  L = arr[start:mid+1]
  R = arr[mid+1:end+1]
  m = n = 0
  k = start

  while m < len(L) and n < len(R):
    if L[m] < R[n]:
      arr[k] = L[m]
      m += 1
    else:
      arr[k] = R[n]
      n += 1
    k += 1


  ## copying the remaining elements of left subarray
  while m < len(L):
    arr[k] = L[m]
    m = m + 1
    k = k + 1

  ## copying the remaining elements of right subarray
  while n < len(R):
    arr[k] = R[n]
    n = n + 1
    k = k + 1

## function definition of mergeSort
## approach: divide and conquer
def mergeSort(arr, start, end):
  if start < end:
    ## 1. Divide - c
    mid = start + (end - start)//2
    ## 2. Conquer - 2T(n/2)
    ## recursive call for the left subtree
    mergeSort(arr, start, mid)
    ## recursive call for the right subtree
    mergeSort(arr, mid+1, end)
    ## 3. Combine - n
    ## combine the results of both left and right subtree
    mergeProcedure(arr, start, mid, end)

## Driver code
arr = [50, 20, 45, 11, 15, 27, 34]
start = 0
end = len(arr) - 1
n = len(arr)
## function calling
mergeSort(arr, start, end)
## print the elements in the array
for i in range(n):
  print(arr[i], end=' ')

  ```
> APPROACH
## 1. Overview of Merge Sort
Merge Sort is a sorting algorithm that works by:

Dividing the array into two halves.
Recursively sorting each half.
Merging the two sorted halves to produce the final sorted array.
## 2. Code Breakdown
2.1 mergeProcedure Function
The mergeProcedure function merges two sorted subarrays into a single sorted array.

## Parameters:

arr: The array that contains the two subarrays to be merged.
start: The starting index of the left subarray.
mid: The ending index of the left subarray (which is also one less than the starting index of the right subarray).
end: The ending index of the right subarray.
Steps:

## Create Subarrays:

L = arr[start:mid+1]: This creates the left subarray.
R = arr[mid+1:end+1]: This creates the right subarray.
Merge Subarrays:

 Initialize pointers m and n to 0 (for L and R respectively), and k to start.
Compare elements from L and R. Place the smaller element in arr[k] and increment the respective pointer and k.
Copy Remaining Elements:

After one of the subarrays is exhausted, copy the remaining elements from the other subarray to arr.
2.2 mergeSort Function
The mergeSort function sorts an array using the merge sort algorithm.

### Parameters:

arr: The array to be sorted.
start: The starting index of the portion of the array to be sorted.
end: The ending index of the portion of the array to be sorted.
Steps:

### Divide:

Calculate the middle index mid as start + (end - start) // 2.
Conquer:

Recursively call mergeSort to sort the left half (arr[start:mid]).
Recursively call mergeSort to sort the right half (arr[mid+1:end]).
Combine:

Call mergeProcedure to merge the two sorted halves into the original array arr.
### 2.3 Driver Code
The driver code initializes the array and calls mergeSort to sort the array.

Steps:

Define an unsorted array arr.
Set the start and end indices for the entire array.
Call mergeSort to sort the array.
Print the sorted array.
3. Complexity Analysis
### Time Complexity:

Divide Step: Each call to mergeSort splits the array into two halves, which is O(log n) divisions.
Conquer Step: Each level of recursion involves merging subarrays, which takes linear time O(n). Therefore, the overall time complexity is O(n log n).
### Space Complexity:

The space complexity is O(n) due to the additional space used for merging (temporary subarrays L and R).

