# All Paths From Source to Target 
## 797. All Paths From Source to Target https://leetcode.com/problems/all-paths-from-source-to-target/description/

Given a directed acyclic graph (DAG) of n nodes labeled from 0 to n - 1, find all possible paths from node 0 to node n - 1 and return them in any order.

The graph is given as follows: graph[i] is a list of all nodes you can visit from node i (i.e., there is a directed edge from node i to node graph[i][j]).

**Example 1:**

![all_1](https://user-images.githubusercontent.com/71955443/210163263-c8af1cda-6ad4-4ba3-b55e-5bb02b79712f.jpg)
```
Input: graph = [[1,2],[3],[3],[]]
Output: [[0,1,3],[0,2,3]]
Explanation: There are two paths: 0 -> 1 -> 3 and 0 -> 2 -> 3.
```

**Example 2:**

![all_2](https://user-images.githubusercontent.com/71955443/210163268-1102c5c2-c00f-4591-a8c4-053cd46763ea.jpg)

```
Input: graph = [[4,3,1],[3,2,4],[3],[4],[]]
Output: [[0,4],[0,3,4],[0,1,3,4],[0,1,2,3,4],[0,1,4]]
```

**Constraints:**

* n == graph.length
* 2 <= n <= 15
* 0 <= graph[i][j] < n
* graph[i][j] != i (i.e., there will be no self-loops).
* All the elements of graph[i] are unique.
* The input graph is guaranteed to be a DAG.

## Solution:

```
class Solution:
    def allPathsSourceTarget(self, graph: List[List[int]]) -> List[List[int]]:
        paths=[]
        def aa(i,path):
            path.append(i)
            if i==len(graph)-1:
                paths.append(path)
                return
            for j in graph[i]:
                tem=[k for k in path]
                aa(j,tem)
        aa(0,[])
        return paths
```
