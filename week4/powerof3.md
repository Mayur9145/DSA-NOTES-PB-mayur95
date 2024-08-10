
## Majority Element

[leetcode](https://leetcode.com/problems/power-of-three/submissions/1349459677/)


## Approach to Determine if a Number is a Power of Three

The goal of this approach is to determine if a given integer `n` is a power of three using a recursive function. 

### Steps in the Approach

1. **Base Case Check:**
   - **Condition:** `n <= 0`
   - **Action:** If `n` is less than or equal to zero, return `False`. This is because negative numbers and zero cannot be powers of three.

2. **Check for Base Power:**
   - **Condition:** `n == 1`
   - **Action:** If `n` is exactly `1`, return `True`. This is because \(3^0 = 1\), which is a valid power of three.

3. **Recursive Case:**
   - **Condition:** `n % 3 == 0`
   - **Action:** If `n` is divisible by `3`, then recursively check if `n / 3` is a power of three. This works because if `n` is a power of three, then dividing it by `3` should also yield a power of three.

4. **Non-Divisible Case:**
   - **Condition:** `n % 3 != 0`
   - **Action:** If `n` is not divisible by `3`, return `False`. This means that `n` cannot be a power of three if it isn't divisible by `3`.

### Example Walkthrough

Let's illustrate this approach with an example where `n = 27`.

1. **Initial Call:**
   - **Input:** `n = 27`
   - **Check:** Since `27 > 0` and `27 % 3 == 0`, proceed to check if `27 / 3 = 9` is a power of three.

2. **Recursive Call 1:**
   - **Input:** `n = 9`
   - **Check:** Since `9 > 0` and `9 % 3 == 0`, proceed to check if `9 / 3 = 3` is a power of three.

3. **Recursive Call 2:**
   - **Input:** `n = 3`
   - **Check:** Since `3 > 0` and `3 % 3 == 0`, proceed to check if `3 / 3 = 1` is a power of three.

4. **Recursive Call 3:**
   - **Input:** `n = 1`
   - **Check:** Since `1 == 1`, return `True`.

### Final Result

The result is `True` because `27` is a power of three (\(3^3 = 27\)).

### Complexity Analysis

- **Time Complexity:** `O(log_3(n))` - The function divides `n` by `3` at each recursive call, so the number of calls is proportional to the logarithm of `n` with base `3`.

- **Space Complexity:** `O(log_3(n))` - The recursion stack depth is proportional to the logarithm of `n` with base `3`, as there are `O(log_3(n))` recursive calls.

This approach efficiently determines if `n` is a power of three using recursion with logarithmic time and space complexity.













```python
class Solution:
    def isPowerOfThree(self, n: int) -> bool:
            if n <= 0:
                return False
    # Base case for n == 1
            if n == 1:
                return True
    # Recursive case: check if n is divisible by 3
            if n % 3 == 0:
                return self.isPowerOfThree(n // 3)
            else:
                return False

# Create an instance of the Solution class
solution = Solution()


# Test case
print(solution.isPowerOfThree(-1))  # Output: False


```



## Example Walkthrough

Let's determine if `27` is a power of three using the provided recursive approach.

### Initial Call

- **Input:** `n = 27`
- **Check:** `27 > 0` and `27 % 3 == 0`
- **Action:** Since `27` is divisible by `3`, we recursively check if `27 / 3 = 9` is a power of three.

### Recursive Call 1

- **Input:** `n = 9`
- **Check:** `9 > 0` and `9 % 3 == 0`
- **Action:** Since `9` is divisible by `3`, we recursively check if `9 / 3 = 3` is a power of three.

### Recursive Call 2

- **Input:** `n = 3`
- **Check:** `3 > 0` and `3 % 3 == 0`
- **Action:** Since `3` is divisible by `3`, we recursively check if `3 / 3 = 1` is a power of three.

### Recursive Call 3

- **Input:** `n = 1`
- **Check:** `1 == 1`
- **Action:** Since `1` is the base case, we return `True`.

### Final Result

The result is `True` because `27` is a power of three (i.e., \(3^3 = 27\)).

## Complexity Analysis

### Time Complexity

- **Time Complexity:** `O(log_3(n))` - Each recursive call divides `n` by `3`, so the number of calls is proportional to the logarithm of `n` with base `3`.

### Space Complexity

- **Space Complexity:** `O(log_3(n))` - Due to the recursion stack, which has depth proportional to `log_3(n)`.
