## 77. Combinations

Given two integers n and k, return all possible combinations of k numbers chosen from the range [1, n].

You may return the answer in any order.

https://leetcode.com/problems/combinations/

---

#### 풀이 1. 

```python
class Solution(object):
    def combine(self, n, k):

        result = []
        elements = []
        def dps(elements, start, k):
            
            if len(elements) == k:
                result.append(elements[:])
                
            for e in range(start, n + 1): 
                elements.append(e)
                dps(elements, e + 1, k)
                elements.pop()
        
        dps(elements, 1, k)
        
        return result
```

---

#### 알게된 점
  + 파이썬 모듈 `itertools.combinations(range(1, n+1), k)` 로 조합을 얻을 수 있음

#### 어려웠던 점
  + 가물가물한 조합의 개념 : n개의 원소를 갖는 집합에서 r개의 원소를 선택하는 것
