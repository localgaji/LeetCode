## 771. Jewels and Stones

You're given strings jewels representing the types of stones that are jewels, and stones representing the stones you have. 
Each character in stones is a type of stone you have. You want to know how many of the stones you have are also jewels.

Letters are case sensitive, so "a" is considered a different type of stone from "A".

---

#### 풀이 1. 리스트 검색 기능


```python
class Solution(object):
    def numJewelsInStones(self, jewels, stones):

        answer = 0
        for i in stones:
            if i in jewels:
                answer += 1

        return answer 
```
---

#### 풀이 2. 해시 문제니까 해시로 풀기


```python
class Solution(object):
    def numJewelsInStones(self, jewels, stones):
        dic = collections.defaultdict(int)
        answer = 0
        for i in stones:
            dic[i] += 1
        
        for j in jewels:
            answer += dic[j]

        return answer 
```

시간 약간 단축, 공간 많이 차지
