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

<p>
Quack quack
<text color=red>ERROR</text>
</p>

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
