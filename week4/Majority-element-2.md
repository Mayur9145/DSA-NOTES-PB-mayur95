

# Majority element-2

[leetcode](https://leetcode.com/problems/majority-element-ii/)

>TC=O(n)

>SC=O(1)





```python

class Solution:
    def majorityElement(self, nums: List[int]) -> List[int]:
        if not nums:
            return []
    
    # Step 1: Identify potential candidates using Boyer-Moore Voting Algorithm
        candidate1, candidate2, count1, count2 = None, None, 0, 0
    
        for num in nums:
            if candidate1 == num:
                count1 += 1
            elif candidate2 == num:
                count2 += 1
            elif count1 == 0:
                candidate1, count1 = num, 1
            elif count2 == 0:
                candidate2, count2 = num, 1
            else:
                count1 -= 1
                count2 -= 1
    
    # Step 2: Validate the candidates by counting their actual occurrences
        result = []
        count1, count2 = 0, 0
    
        for num in nums:
            if num == candidate1:
                count1 += 1
            elif num == candidate2:
                count2 += 1
    
        n = len(nums)
        if count1 > n // 3:
            result.append(candidate1)
        if count2 > n // 3:
            result.append(candidate2)
    
        return result

```

This code solves the problem of finding all elements in an array that appear more than ⌊n/3⌋ times. The Boyer-Moore Voting Algorithm is used to identify potential candidates, and then the candidates are validated.

### Step 1: Identify Potential Candidates
The algorithm uses two candidate variables (candidate1 and candidate2) and their corresponding counts (count1 and count2). The logic to update these candidates and counts is as follows:

If num matches candidate1, increment count1.
If num matches candidate2, increment count2.
If count1 is 0, set candidate1 to num and count1 to 1.
If count2 is 0, set candidate2 to num and count2 to 1.
If none of the above conditions are met, decrement both count1 and count2.
By the end of the loop, candidate1 and candidate2 are potential majority elements.

### Step 2: Validate the Candidates
After the potential candidates are identified, the code counts their actual occurrences in the array. If a candidate appears more than ⌊n/3⌋ times, it is added to the result list.

### Example Walkthrough
Consider the array nums = [3, 2, 3, 2, 3, 2, 3].

Initial Variables: candidate1 = None, candidate2 = None, count1 = 0, count2 = 0.

Iteration 1 (num = 3):

count1 is 0, so candidate1 becomes 3, and count1 becomes 1.
Iteration 2 (num = 2):

count2 is 0, so candidate2 becomes 2, and count2 becomes 1.
Iteration 3 (num = 3):

num matches candidate1, so count1 becomes 2.
Iteration 4 (num = 2):

num matches candidate2, so count2 becomes 2.
Iteration 5 (num = 3):

num matches candidate1, so count1 becomes 3.
Iteration 6 (num = 2):

num matches candidate2, so count2 becomes 3.
Iteration 7 (num = 3):

num matches candidate1, so count1 becomes 4.
By the end of the loop, candidate1 = 3 and candidate2 = 2 are identified as potential majority elements.

Validation Phase:

The code counts the occurrences of 3 and 2. Both appear 4 times, and since 4 > 7//3 (which is 2), both 3 and 2 are added to the result list.
The final output is [3, 2].