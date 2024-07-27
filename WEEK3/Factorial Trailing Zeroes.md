#Factorial Trailing Zeroes
##Week-3 Assignment Question

[leetcode](https://leetcode.com/problems/factorial-trailing-zeroes/description/?envType=study-plan-v2&envId=top-interview-150)


**Time complexity -O(log~5~n) **

**Space complexity -O(1)**


`> Below `Code  in  Python`

##Coding explanation
###Initialize count: This will hold the number of trailing zeroes.

###Set power_of_5 to 5: We start with the first power of 5.
###While loop: Continue as long as n is greater than or equal to the current power_of_5.
###n // power_of_5: This gives the number of multiples of the current power of 5 in the range from 1 to 𝑛

###Add this count to count.
###Multiply power_of_5 by 5: Move to the next power of 5.
###Return count: This is the total number of trailing zeroes in 𝑛!






```python
class Solution:
    def trailingZeroes(self, n: int) -> int:
        count_of_tzero = 0
        power_of_5 = 5
        while n >= power_of_5:
            count_of_tzero += n // power_of_5
            power_of_5 *= 5
        return count_of_tzero
```

###Problem Statement-
Given an integer n, return the number of trailing zeroes in n!.

Note that n! = n * (n - 1) * (n - 2) * ... * 3 * 2 * 1.

 

Example 1:

Input: n = 3
Output: 0
Explanation: 3! = 6, no trailing zero.
Example 2:

Input: n = 5
Output: 1
Explanation: 5! = 120, one trailing zero.
Example 3:

Input: n = 0
Output: 0
 

Constraints:

0 <= n <= 104

**Trailing Zero concept**

Definition: Trailing zeroes in a number are the zeroes at the end of the number. For example, the number 100 has two trailing zeroes.

Cause of Trailing Zeroes: Trailing zeroes are produced by factors of 10 in the number. Since 10 is the product of 2 and 5, we need to count the pairs of 2s and 5s in the factorization of 
𝑛
!
n!.

Counting Factors of 2 and 5:

###Every multiple of 5 contributes at least one factor of 5.
###Every multiple of 25 contributes an extra factor of 5 (since 25=5^2).
###Every multiple of 125 contributes yet another factor of 5 (since 125=5^3)

##Approach
**Initialize a counter for trailing zeroes.**

**Iterate through the powers of 5:**

**For each power, count how many multiples of that power are present in the numbers from 1 to n**

**Add these counts to the trailing zeroes counter.
Stop when the power of 5 exceeds 
𝑛
n.**

















