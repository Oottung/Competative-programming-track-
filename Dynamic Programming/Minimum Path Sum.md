# Minimum Path Sum
## 64. Minimum Path Sum

Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right, which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.

**Example 1:**

![minpath](https://user-images.githubusercontent.com/71955443/210150528-8e2a3f17-7acf-4c82-9406-99be59be24e2.jpg)


```
Input: grid = [[1,3,1],[1,5,1],[4,2,1]]
Output: 7
Explanation: Because the path 1 → 3 → 1 → 1 → 1 minimizes the sum.
```

**Example 2:**
```
Input: grid = [[1,2,3],[4,5,6]]
Output: 12
```
**Constraints:**
```
m == grid.length
n == grid[i].length
1 <= m, n <= 200
0 <= grid[i][j] <= 100
```

**Related Topics:** Array DP Matrix

## **Solution:**

```
class Solution:
    def minPathSum(self, grid: List[List[int]]) -> int:
        cos=[[0]*len(grid[0]) for i in range(len(grid))]
        r=len(grid)
        c=len(grid[0])

        for i in range(r):
            for j in range(c):
                if j==0 and i==0:
                    cos[0][0]=grid[0][0]
                elif i==0:
                    cos[0][j]=cos[0][j-1]+grid[0][j]
                elif j==0:
                    cos[i][0]=cos[i-1][0]+grid[i][0]
                else:
                    cos[i][j]=min(cos[i-1][j],cos[i][j-1])+grid[i][j]
        print(cos)
        return cos[-1][-1]
```
 
