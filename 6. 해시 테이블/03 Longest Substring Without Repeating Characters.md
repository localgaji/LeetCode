## 3. Longest Substring Without Repeating Characters


Given a string s, find the length of the longest 
substring
 without repeating characters.


---

#### 풀이 1. 슬라이딩 윈도우

1. 

```python
class Solution(object):
    def lengthOfLongestSubstring(self, s):

        maxlength = 0
        l, r = 0, 0
        
        if len(s) <= 1:
            return len(s)

        while r <= len(s) - 2:
            longest = [s[l]]
            while r < len(s) - 1 and not s[r+1] in longest:
                r += 1
                longest.append(s[r])
                
            maxlength = max(r - l + 1, maxlength)

            l += 1
            r = l
            
        return maxlength
```

시간이 다소 소요됨 (1894 ms)

---

#### 풀이 2. 해시 테이블 


```python
class Solution(object):
    def lengthOfLongestSubstring(self, s):

        maxlength = 0
        left = 0
        dic = {}
        
        for i, x in enumerate(s):
        
            if x in dic and dic[x] >= left:
                left = dic[x] + 1
            else:
                maxlength = max(i - left + 1 , maxlength)
        
            dic[x] = i

        return maxlength
```

36 ms
