#Find First and Last Position of Element in Sorted Array
## Assignment Problem WEEK 3


[leetcode](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/description/?envType=study-plan-v2&envId=top-interview-150)

>**DESCRIPTION**

Given an array of integers nums sorted in non-decreasing order, find the starting and ending position of a given target value.

If target is not found in the array, return [-1, -1].

You must write an algorithm with O(log n) runtime complexity.

 

Example 1:

Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]
Example 2:

Input: nums = [5,7,7,8,8,10], target = 6
Output: [-1,-1]
Example 3:

Input: nums = [], target = 0
Output: [-1,-1]
 

Constraints:

0 <= nums.length <= 105
-109 <= nums[i] <= 109
nums is a non-decreasing array.
-109 <= target <= 109

>`PYTHON CODE`

**Time Complexity-O(log n)**

**Space Complexity-O(1)**

```Python
class Solution:
    def searchRange(self, nums: List[int], target: int) -> List[int]:
        def findFirst(nums, target):
            left, right = 0, len(nums) - 1
            first_position = -1
            while left <= right:
                mid = (left + right) // 2
                if nums[mid] < target:
                    left = mid + 1
                elif nums[mid] > target:
                    right = mid - 1
                else:
                    first_position = mid
                    right = mid - 1  # Continue to search in the left half
            return first_position

        def findLast(nums, target):
            left, right = 0, len(nums) - 1
            last_position = -1
            while left <= right:
                mid = (left + right) // 2
                if nums[mid] < target:
                    left = mid + 1
                elif nums[mid] > target:
                    right = mid - 1
                else:
                    last_position = mid
                    left = mid + 1  # Continue to search in the right half
            return last_position

        first_position = findFirst(nums, target)
        last_position = findLast(nums, target)

        return [first_position, last_position]

        

```


## `Approach`
### Binary Search for First Position:

### We initialize left to 0 and right to the last index of the array.
### Use a while loop to perform binary search until left exceeds right.
### Calculate the middle index mid.
### If the element at mid is less than the target, move the left pointer to mid + 1.
###  If the element at mid is greater than the target, move the right pointer to mid - 1.
### If the element at mid equals the target, record mid as the first position and move the right pointer to mid - 1 to continue searching in the left half.
### Binary Search for Last Position:

### Similar to the first binary search, but this time we adjust the pointers to continue searching in the right half when we find the target.
### If the element at mid equals the target, record mid as the last position and move the left pointer to mid + 1.

### Combine Results
### After both binary searches, return the recorded positions as a list [first_position, last_position].


