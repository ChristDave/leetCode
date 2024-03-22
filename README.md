# leetCode

#### Here are some leetCode i solved including the language used and the % of the effectiveness 
* Longest Palindromic Substring <br>
level: Medium <br>
Given a string s, return the longest palindromic substring in s. <br> <br>

Example 1: <br>
Input: s = "babad" <br>
Output: "bab" <br>
Explanation: "aba" is also a valid answer. <br> < br>

Example 2: <br>
Input: s = "cbbd" <br>
Output: "bb" <br> <br>

Constraints: < br/> 

1 <= s.length <= 1000 <br>
s consist of only digits and English letters. <br>
```
language: python
%: 63
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

5. Longest Palindromic Substring
level: Medium
Given a string s, return the longest palindromic substring in s.

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
