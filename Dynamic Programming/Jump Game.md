# Jump Game
## 55. Jump Game

You are given an integer array nums. You are initially positioned at the array's first index, and each element in the array represents your maximum jump length at that position.

Return true if you can reach the last index, or false otherwise.

**Example 1:**
```
Input: nums = [2,3,1,1,4]
Output: true
Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.
```
**Example 2:**
```
Input: nums = [3,2,1,0,4]
Output: false
Explanation: You will always arrive at index 3 no matter what. Its maximum jump length is 0, which makes it impossible to reach the last index.
```
Constraints:

```
1 <= nums.length <= 104
```
```
0 <= nums[i] <= 105
```



Solution:


1. First I tried using recursion and dp with memoization but that resulted in TLE.
The code for that:
```
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        dp=[-1]*len(nums)
        def a(i):
            if i==len(nums)-1:
                return True
            else:
                
                if dp[i]!=-1:
                    return dp[i]
                ans=False
                for j in range(nums[i]):
                    ans=ans or a(i+j+1)
                    if ans==True:
                        dp[i]=True
                        return True
                dp[i]=ans
                return dp[i]
        return a(0)
```

2. The Greedy solution. We don't need to care about all the other paths as we just need to find if it's possible to reach the end.
```
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        
        farr=0
        for i,j in enumerate(nums):
            if farr<i: return False
            farr=max(farr,i+j)

        return True
```
