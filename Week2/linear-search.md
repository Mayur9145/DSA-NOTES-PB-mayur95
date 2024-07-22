
# Linear Search

# This is an important concepts in dsa-batch-2.0

We are given an array of elements and our task is to find a specific target from that array of elements

# Approache
We will take a for loop and start scanning the array from left to right 

Then every time we scan we are going to check in a if condition that the desired target exist in the array or not

If the target exists then we will return the inidex number of the target in the array [We will return the index number according to the question either o based or 1 based indexing]

If suppose we scanned the entire array but not found the element then we will say that  the elment doesn't exist in the array.
## Demo

https://colab.research.google.com/drive/1YaNIrUoCMyXzBVgXoIkLI5vuDl5I1HX6




## Code
Linear Search

Time Complexity: O(n)

Space Complexity: O(1)|
## function definition
# def linearSearch(arr, n, target):
  for i in range(n):
    if arr[i] == target:
      return i
  ## target element is not available in the array
  return -1

## Driver code
arr = [12, 14, 11, 29, 31, 45, 62]
target = 63
n = len(arr)
result = linearSearch(arr, n, target)
print(result)
