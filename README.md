# LeetCode

#### Here are some leetCode i solved including the language used and the % of the effectiveness 
### 1 - Longest Palindromic Substring 

  
**level: Medium** <br> <br>
```
Given a string s, return the longest palindromic substring in s. <br> <br>

Example 1: 
Input: s = "babad"
Output: "bab" 
Explanation: "aba" is also a valid answer. 

Example 2: 
Input: s = "cbbd" 
Output: "bb" 

Constraints:

1 <= s.length <= 1000
s consist of only digits and English letters. 
```
**Solution: <br> 
language: python <br>
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
---
### 2 - Two Sums
**level: Medium** <br> <br>
```
Given an array of integers nums and an integer target,
return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution,
and you may not use the same element twice. 

You can return the answer in any order.

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
**Solution: <br> 
language: python <br>
%: 63**
---

### 3 - Zigzag Conversion
**level: Medium** <br> <br>
```
The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this:
(you may want to display this pattern in a fixed font for better legibility)

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

**Solution 2:** <br> 
**language: python** <br>
```
class Solution:
    def convert(self, s: str, numRows: int) -> str:
        if(numRows  < 2):
            return s
        arr = ['' for i in range(numRows)]
        direction = 'down'
        row = 0
        for i in s:
            arr[row] += i
            if row == numRows-1:
                direction = 'up'
            elif row == 0:
                direction = 'down'
            if(direction == 'down'):
                row += 1
            else:
                row -= 1
        return(''.join(arr))
```

**Note:**
```
- initialize an empty matrix with x rows and y columns
matrix = [["" for _ in range(y)] for _ in range(x)]

- join a list with what's inside the quote
''.join(matrix)
```
---

### 4 - Reverse Integer
  
**level: Medium** <br> <br>
```
Given a signed 32-bit integer x, return x with its digits reversed.
If reversing x causes the value to go outside the signed 32-bit integer range [-2^31, 2^31 - 1], then return 0.

Assume the environment does not allow you to store 64-bit integers (signed or unsigned). 

Example 1:

Input: x = 123
Output: 321

Example 2:

Input: x = -123
Output: -321

Example 3:

Input: x = 120
Output: 21

Constraints:

    -2^31 <= x <= 2^31 - 1

```
**Solution: <br> 
language: python <br>
%: 86.35**

```
class Solution:
    import math
    def reverse(self, x: int) -> int:
        res = ""
        xStr = str(x)
        if xStr[0] == "-":
            for i in range(len(xStr)-1,0,-1):
                res = res + xStr[i]

            res = "-" + res
        else:
            for i in range(len(xStr)-1,-1,-1):
                res = res + xStr[i]

        res = int(res)

        if res > math.pow(2,31) - 1 or res < math.pow(-2,31):
            res = 0

        return res
```
**Solution2: 
language: python**

```
class Solution:
    def reverse(self, x: int) -> int:

        rev = abs(x) # get an absolute value
        rev = str(rev) # turn it into a string
        rev = rev[::-1] # reverse the number while it's a string
        rev = int(rev) # turn it into an integer again

        if rev.bit_length() < 32:
            if x < 0:
                return -rev
            else:
                return rev
        else:
            return 0
``` 

**Note:**
```
- convert int to string
x = str(x)

- convert string to int
x = int(x)

- reverse the number while it's a string
rev = rev[::-1]

- bit_length() returns the number of bits required to represent the integer
let x be a int:
x.bit_length()
```
---

### 5 - Reformat Date 

  
**level: Easy** <br> <br>
```
Given a date string in the form Day Month Year, where: <br>

Day is in the set {"1st", "2nd", "3rd", "4th", ..., "30th", "31st"}.
Month is in the set {"Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"}.
Year is in the range [1900, 2100].
Convert the date string to the format YYYY-MM-DD, where:

YYYY denotes the 4 digit year.
MM denotes the 2 digit month.
DD denotes the 2 digit day.
 

Example 1:

Input: date = "20th Oct 2052"
Output: "2052-10-20"

Example 2:

Input: date = "6th Jun 1933"
Output: "1933-06-06"

Example 3:

Input: date = "26th May 1960"
Output: "1960-05-26"
```
**Solution :
language: python
%: 85**

```
class Solution:
  def date(s):
    parts = s.split()
    
    # Extract day using string methods 
    day_str = parts[0].rstrip('stndrh')  # Remove common ordinal suffixes
    day = day_str.zfill(2)  # Zero-pad to 2 digits
    
    months = {
        'Jan': '01', 'Feb': '02', 'Mar': '03', 'Apr': '04',
        'May': '05', 'Jun': '06', 'Jul': '07', 'Aug': '08',
        'Sep': '09', 'Oct': '10', 'Nov': '11', 'Dec': '12'
    }
    
    return f"{parts[2]}-{months[parts[1]]}-{day}"
```

**Note:**
```
- rstrip("xxxx"), Removes characters from the end until it finds a character not in the specified set
day = "20th"
day = day.rstrip("th")  ~~ day => 20

- rstrip(), If no argument given, removes whitespace
"45 ".rstrip() -> "45"

- zfill(), Adds '0' characters to the left until the string reaches the specified length
"5".zfill(2) → "05" (ensures 2-digit format)

```
---
