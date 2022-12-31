# Unique Paths III
## 980 Unique Paths III https://leetcode.com/problems/unique-paths-iii/description/

You are given an m x n integer array grid where grid[i][j] could be:
* 1 representing the starting square. There is exactly one starting square.
* 2 representing the ending square. There is exactly one ending square.
* 0 representing empty squares we can walk over.
* -1 representing obstacles that we cannot walk over.
Return the number of 4-directional walks from the starting square to the ending square, that walk over every non-obstacle square exactly once.

Example 1:

![lc-unique1](https://user-images.githubusercontent.com/71955443/210150373-4cafb2bc-9f5a-4f7a-9e36-09495d690c36.jpg)

```
Input: grid = [[1,0,0,0],[0,0,0,0],[0,0,2,-1]]
Output: 2
Explanation: We have the following two paths: 
1. (0,0),(0,1),(0,2),(0,3),(1,3),(1,2),(1,1),(1,0),(2,0),(2,1),(2,2)
2. (0,0),(1,0),(2,0),(2,1),(1,1),(0,1),(0,2),(0,3),(1,3),(1,2),(2,2)
```

Example 2:

![lc-unique2](https://user-images.githubusercontent.com/71955443/210150400-c3764452-1deb-448a-8ea6-280ad0b27930.jpg)

```
Input: grid = [[1,0,0,0],[0,0,0,0],[0,0,0,2]]
Output: 4
Explanation: We have the following four paths: 
1. (0,0),(0,1),(0,2),(0,3),(1,3),(1,2),(1,1),(1,0),(2,0),(2,1),(2,2),(2,3)
2. (0,0),(0,1),(1,1),(1,0),(2,0),(2,1),(2,2),(1,2),(0,2),(0,3),(1,3),(2,3)
3. (0,0),(1,0),(2,0),(2,1),(2,2),(1,2),(1,1),(0,1),(0,2),(0,3),(1,3),(2,3)
4. (0,0),(1,0),(2,0),(2,1),(1,1),(0,1),(0,2),(0,3),(1,3),(1,2),(2,2),(2,3)
```

Example 3:

![lc-unique3-](https://user-images.githubusercontent.com/71955443/210150420-70f68756-2b7c-4e86-8f91-7b0b356506de.jpg)

```
Input: grid = [[0,1],[2,0]]
Output: 0
Explanation: There is no path that walks over every empty square exactly once.
Note that the starting and ending square can be anywhere in the grid.
```

Constraints:

* m == grid.length
* n == grid[i].length
* 1 <= m, n <= 20
* 1 <= m * n <= 20
* -1 <= grid[i][j] <= 2
* There is exactly one starting cell and one ending cell.

## Solution:

```
class Solution:
    def uniquePathsIII(self, grid: List[List[int]]) -> int:
        r,c=len(grid),len(grid[0])
        sqs=-2
        for i in range(r):
            for j in range(c):
                if grid[i][j]!=-1:
                    sqs+=1
                if grid[i][j]==1:
                    starty,startx=j,i
        vis=[[0]*c for i in range(r)]
        def bound(x,y):
            return x>=0 and y>=0 and x<r and y<c
        def aa(x,y,c):
            if bound(x,y) and grid[x][y]!=-1 and vis[x][y]==0:
                vis[x][y]=1
                if grid[x][y]==2 and c==sqs+1:
                    ans = 1
                elif grid[x][y]==2:
                    ans = 0
                else:
                    ans=aa(x+1,y,c+1)+aa(x-1,y,c+1)+aa(x,y-1,c+1)+aa(x,y+1,c+1)
                vis[x][y]=0
                return ans
            return 0
        return aa(startx,starty,0)

```
