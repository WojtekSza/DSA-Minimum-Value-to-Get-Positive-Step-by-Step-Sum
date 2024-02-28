# DSA-Minimum-Value-to-Get-Positive-Step-by-Step-Sum
Given an array of integers nums, you start with an initial positive value startValue.

In each iteration, you calculate the step by step sum of startValue plus elements in nums (from left to right).

Return the minimum positive value of startValue such that the step by step sum is never less than 1.
```
Input: nums = [-3,2,-3,4,2]
Output: 5
Explanation: If you choose startValue = 4, in the third iteration your step by step sum is less than 1.
step by step sum
startValue = 4 | startValue = 5 | nums
  (4 -3 ) = 1  | (5 -3 ) = 2    |  -3
  (1 +2 ) = 3  | (2 +2 ) = 4    |   2
  (3 -3 ) = 0  | (4 -3 ) = 1    |  -3
  (0 +4 ) = 4  | (1 +4 ) = 5    |   4
  (4 +2 ) = 6  | (5 +2 ) = 7    |   2
```
```
class Solution:
    def minStartValue(self, nums: List[int]) -> int:
        n=len(nums)
        prefix=[nums[0]]
        for i in range(1,n):
            prefix.append(nums[i]+prefix[-1])                 
        min_val = 0
        for j in range(n):
            min_val=min(min_val,prefix[j])
        return -min_val + 1

```
