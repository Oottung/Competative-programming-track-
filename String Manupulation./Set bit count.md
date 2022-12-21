# Set Bit Count
## Hackerearth question

You are given a binary string **S**. You need to determine the number of **substrings** of **S** that would have atleast **X** set bits.

**Input format:**
1. The first line consists of the binary string **S**.
2. The second line consists of a single integer **X**.

**Output format:**
Print the required answer in a new line.


## **Solution:**

```

# Boilerplate code:
st=input()
x=int(input())

#Solution:
l=len(st)
ans=0    
for i in range(l):
    c=0
    for j in range(i,l):
        if c>=x:
            ans+=1
        if st[j]=="1":
            c+=1
    if c>=x:
        ans+=1
print(ans)

```
