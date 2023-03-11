## 46. Permutations

Given an array nums of distinct integers, return all the possible permutations. You can return the answer in any order.

https://leetcode.com/problems/permutations/

---

#### 풀이 1. DFS 재귀 구조 

```python
class Solution(object):
    def permute(self, nums):

        answer, prev = [], []

        def dps(elements):

            if elements == []:
                answer.append(prev[:]) 
                #list는 가변객체, prev가 변경되면 answer도 변경되므로 슬라이싱으로 복사
            
            for e in elements:
                nexte = elements[:]
                nexte.remove(e)
                prev.append(e)

                dps(nexte)
                prev.pop()

        dps(nums)

        return answer
```
---

#### 알게된 점
  + list는 가변객체이므로 슬라이싱으로 복사한다

#### 어려웠던 점
  + 책에 나온 풀이를 한 단계씩 살펴보면 이해는 되지만 재귀 구조가 직관적으로 와닿지 않아 문제를 보고 바로 풀이를 떠올리기 힘들것 같다.  
