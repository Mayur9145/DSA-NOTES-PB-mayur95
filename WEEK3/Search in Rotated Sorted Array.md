#Search in Rotated Sorted Array
## Assignment problem week 3

[leetcode](https://leetcode.com/problems/search-in-rotated-sorted-array/?envType=study-plan-v2&envId=top-interview-150)

**DESCRIPTION**

There is an integer array nums sorted in ascending order (with distinct values).

Prior to being passed to your function, nums is possibly rotated at an unknown pivot index k (1 <= k < nums.length) such that the resulting array is [nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]] (0-indexed). For example, [0,1,2,4,5,6,7] might be rotated at pivot index 3 and become [4,5,6,7,0,1,2].

Given the array nums after the possible rotation and an integer target, return the index of target if it is in nums, or -1 if it is not in nums.

You must write an algorithm with O(log n) runtime complexity.

 

Example 1:

Input: nums = [4,5,6,7,0,1,2], target = 0
Output: 4
Example 2:

Input: nums = [4,5,6,7,0,1,2], target = 3
Output: -1
Example 3:

Input: nums = [1], target = 0
Output: -1
 

Constraints:

1 <= nums.length <= 5000
-104 <= nums[i] <= 104
All values of nums are unique.
nums is an ascending array that is possibly rotated.
-104 <= target <= 104


**Time Complexity-O(logn)**

**Space Complexity-O(1)**



>`Python code`

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left, right = 0, len(nums) - 1  # Initialize right to len(nums) - 1
        while left <= right:
            mid = (left + right) // 2
            
            # Check if mid is the target
            if nums[mid] == target:
                return mid
            
            # Determine the sorted side
            if nums[left] <= nums[mid]:  # Left side is sorted
                if nums[left] <= target < nums[mid]:  # Target in the left side
                    right = mid - 1
                else:  # Target in the right side
                    left = mid + 1
            else:  # Right side is sorted
                if nums[mid] < target <= nums[right]:  # Target in the right side
                    left = mid + 1
                else:  # Target in the left side
                    right = mid - 1
                
        # Target not found
        return -1


```

>**Approach With Example**
###Initialization: Start with two pointers, left and right, set to the beginning and the end of the array, respectively.
###Binary Search Loop:
###Calculate the middle index, mid.
###Check if the middle element is equal to the target. If so, return the middle index.
###Determine which side of the array is properly sorted:
###If the left side is sorted (nums[left] <= nums[mid]):
###Check if the target lies within this range (nums[left] <= target < nums[mid]). If so, move the right pointer to mid - 1. Otherwise, move the left pointer to mid + 1.
###If the right side is sorted (nums[mid] <= nums[right]):
###Check if the target lies within this range (nums[mid] < target <= nums[right]). If so, move the left pointer to mid + 1. Otherwise, move the right pointer to mid - 1.
###Return -1: If the loop terminates without finding the target, return -1.
###Consider the array [4, 5, 6, 7, 0, 1, 2] and target 0:

###Initial State:

###left = 0, right = 6
###mid = (0 + 6) // 2 = 3
###nums[mid] = 7
###Since nums[left] <= nums[mid] (4 <= 7), the left side is sorted.

###Target 0 is not in the range 4 <= target < 7, so move left to mid + 1 = 4.
###Next Iteration:

###left = 4, right = 6
###mid = (4 + 6) // 2 = 5
###nums[mid] = 1
###Since nums[mid] <= nums[right] (1 <= 2), the right side is sorted.

###Target 0 is in the range 0 <= target < 1, so move right to mid - 1 = 4.
###Next Iteration:

###left = 4, right = 4
###mid = (4 + 4) // 2 = 4
###nums[mid] = 0
###Since nums[mid] == target, return mid, which is 4.

###The code will correctly return 4, the index of the target 0.

##This approach ensures the search is performed in O(log n) time, which is the requirement for this problem.