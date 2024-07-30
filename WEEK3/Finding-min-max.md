# Finding max and min in every step at 
# the end returning the final max and min using DIVIDE AND CONQUER


## Time Complexity-O(n)
## Space Complexity-O(log n)
```python 
nums = [12, 24, 10, 21, 65, 42]
low = 0
high = len(nums) - 1

def minmax(nums, low, high):
    if low == high:
        min_val = nums[low]
        max_val = nums[low]
    elif low == high - 1:
        if nums[low] < nums[high]:
            max_val = nums[high]
            min_val = nums[low]
        else:
            max_val = nums[low]
            min_val = nums[high]
    else:
        mid = low + (high - low) // 2
        min1, max1 = minmax(nums, low, mid)
        min2, max2 = minmax(nums, mid + 1, high)
    
        if min1 < min2:
            min_val = min1
        else:
            min_val = min2
        
        if max1 > max2:
            max_val = max1
        else:
            max_val = max2
    
    return (min_val, max_val)

min_val, max_val = minmax(nums, low, high)
print(f"Minimum value: {min_val}, Maximum value: {max_val}")
```

## Approach

The minmax function uses a divide-and-conquer strategy to find the minimum and maximum values in an array. Here’s a step-by-step breakdown of the approach:

Base Case (Single Element): If the subarray has only one element (low == high), both the minimum and maximum values are that element.

Base Case (Two Elements): If the subarray has two elements (low == high - 1), compare the two elements and assign the smaller one as the minimum and the larger one as the maximum.

Recursive Case: If the subarray has more than two elements:

Split the array into two halves.
Recursively find the minimum and maximum values in each half.
Combine the results by taking the minimum of the minimums and the maximum of the maximums from the two halves.


    


        
    
    
