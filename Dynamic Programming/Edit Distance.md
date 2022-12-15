# Edit Distance
## https://www.geeksforgeeks.org/edit-distance-dp-5/

Given two strings str1 and str2 and below operations that can be performed on str1. 
Find minimum number of edits (operations) required to convert ‘str1’ into ‘str2’.  

1. Insert
2. Remove
3. Replace

All of the above operations are of equal cost.
**Examples:**
```
Input:   str1 = “geek”, str2 = “gesek”
Output:  1
Explanation: We can convert str1 into str2 by inserting a ‘s’.
```
```
Input:   str1 = “cat”, str2 = “cut”
Output:  1
Explanation: We can convert str1 into str2 by replacing ‘a’ with ‘u’.
```
```
Input:   str1 = “sunday”, str2 = “saturday”
Output:  3
Explanation: Last three and first characters are same.  
We basically need to convert “un” to “atur”.  
This can be done using below three operations. Replace ‘n’ with ‘r’, insert t, insert a
```

## **Solution:**

Simple Recursion code:
```
class Solution:
    def editDistance(self, s, t):
        def rec(s,t,i,j):
            if i==0:
                return j
            if j==0: 
                return i
            if s[i-1]==t[j-1]: 
                return rec(s,t,i-1,j-1)
            else:
                return 1+min(rec(s,t,i-1,j-1),rec(s,t,i-1,j),rec(s,t,i,j-1))
                   
        ans=rec(s,t,len(s)-1,len(t)-1)
        return ans
```


