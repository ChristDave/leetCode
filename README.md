# LeetCode

#### Here are some leetCode i solved including the language used and the % of the effectiveness 
### 1 - Longest Palindromic Substring 

  
**level: Medium** <br> <br>
```
Given a string s, return the longest palindromic substring in s. <br> <br>

Example 1: <br>
Input: s = "babad" <br>
Output: "bab" <br>
Explanation: "aba" is also a valid answer. <br> < br>

Example 2: <br>
Input: s = "cbbd" <br>
Output: "bb" <br> <br>

Constraints: <br> 

1 <= s.length <= 1000 <br>
s consist of only digits and English letters. <br>
```
**Solution :
language: python
%: 63**

```
class Solution:
  def longestPalindrome(self, s: str) -> str:
      if len(s) == 1:
            return s

      l = []
      for i in range(0,len(s)-1):
          res = ""
          for j in range(len(s)-1,i,-1):
              res = ""
              count = True
              if s[i] == s[j]:
                  res += s[i]
                  if j == i+1:
                      res += s[i]
                      l.append(res)
                  else:
                      a = i
                      b = j
                      while b >= a+1 and count:
                          a+=1
                          b-=1
                          if s[a] != s[b]:
                              count = False
                              res = ""
                                
                      if count:
                          res = ""
                          for k in range(i,j+1):
                              res += s[k]
                          l.append(res)
          
      if len(l) != 0:
          maxi = ""
          for i in l:
              if len(i)>len(maxi):
                  maxi = i
          return maxi
      return s[0]
```

### 2 - Two Sums
**level: Medium** <br> <br>
```
   Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target. <br>

You may assume that each input would have exactly one solution, and you may not use the same element twice. <br>

You can return the answer in any order. <br> <br>

 

Example 1:

Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
Example 2:

Input: nums = [3,2,4], target = 6
Output: [1,2]
Example 3:

Input: nums = [3,3], target = 6
Output: [0,1]
```
**Solution:
language: python
%: 63**
```
```

### 3 - Zigzag Conversion
**level: Medium** <br> <br>
```
The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

P   A   H   N
A P L S I I G
Y   I   R
And then read line by line: "PAHNAPLSIIGYIR"

Write the code that will take a string and make this conversion given a number of rows:

string convert(string s, int numRows);
 

Example 1:

Input: s = "PAYPALISHIRING", numRows = 3
Output: "PAHNAPLSIIGYIR"
Example 2:

Input: s = "PAYPALISHIRING", numRows = 4
Output: "PINALSIGYAHRPI"
Explanation:
P     I    N
A   L S  I G
Y A   H R
P     I
Example 3:

Input: s = "A", numRows = 1
Output: "A"

Constraints:

1 <= s.length <= 1000
s consists of English letters (lower-case and upper-case), ',' and '.'.
1 <= numRows <= 1000
 
```
**Solution: <br> 
language: python <br>
%: 63**
```
class Solution:
    def convert(self, s: str, numRows: int) -> str:
        if len(s) <= numRows:
            return s
        
        if numRows == 1:
            return s
            
        # Find the number of columns
        tail = 1
        count = 1
        numCols = 1
        while count < len(s):  
            count = count + 1
            tail = tail + 1
            if tail == numRows:
                while tail != 1 and count < len(s):
                    count = count + 1
                    tail = tail - 1
                    numCols = numCols + 1
                                  
        return s
        # populate the matrix
        tail = 0
        count = 0
        i = 0
        l = [["" for _ in range(numCols)] for _ in range(numRows)]
        while i < numCols:
            j = 0
            while j < numRows and count < len(s):    
                if tail == j:   #tail is like a pointer to the back 
                    l[j][i] = s[count]        
                    count = count + 1
                    tail = tail + 1
                    j = j + 1
                    if tail == numRows:
                        tail = tail - 2
                        while tail != 0 and count < len(s): # handle the diagonal
                            i = i + 1
                            l[tail][i] = s[count]
                            tail = tail - 1
                            count = count + 1
                            
            i = i + 1
                        
        res = ""
        for i in range(numRows):
            for j in range(numCols):
                res = res + l[i][j]

        return res
```

**Learn:**
```
- initialize an empty matrix with x rows and y columns
matrix = [["" for _ in range(y)] for _ in range(x)]
```

