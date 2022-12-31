# Domino and Tromino Tiling
## 790. Domino and Tromino Tiling (https://leetcode.com/problems/domino-and-tromino-tiling/description/)

You have two types of tiles: a 2 x 1 domino shape and a tromino shape. You may rotate these shapes.

![lc-domino](https://user-images.githubusercontent.com/71955443/210150467-2be80d05-f2b6-4e08-bb3c-8c03c174e292.jpg)

Given an integer n, return the number of ways to tile an 2 x n board. Since the answer may be very large, return it modulo 109 + 7.

In a tiling, every square must be covered by a tile. 
Two tilings are different if and only if there are two 4-directionally adjacent cells on the 
board such that exactly one of the tilings has both squares occupied by a tile.


**Example 1:**
```
Input: n = 3
Output: 5
Explanation: The five different ways are show below.
```

![lc-domino1](https://user-images.githubusercontent.com/71955443/210150484-cf3f4b23-8ec3-4050-a345-698e874a3b22.jpg)


**Example 2:**
```
Input: n = 1
Output: 1
```


## Solution:

DP tabulation:
```
class Solution:
    def numTilings(self, n: int) -> int:
        if n==0: return 0
        if n==1: return 1
        if n==2: return 2
        if n==3: return 5
        dp=[0]*(n+1)
        dp[1]=1
        dp[2]=2
        dp[3]=5
        for i in range(4,n+1):
            dp[i]=2*dp[i-1]+dp[i-3]
        return dp[n]%(10**9+7)

```
