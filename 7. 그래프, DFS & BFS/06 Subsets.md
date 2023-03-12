## 78. Subsets

Given an integer array nums of unique elements, return all possible 
subsets (the power set).

The solution set must not contain duplicate subsets. Return the solution in any order.

https://leetcode.com/problems/subsets/description/

---

#### 풀이 1. 

```python
class Solution(object):
    def subsets(self, nums):
        answer = []

        def dfs(index, subset): 
        # index : for에서 순회할 시작 위치
        # subset : 부분집합이 저장될 리스트
        
            answer.append(subset[:])
            
            # 시작 위치가 리스트를 초과했다면 함수를 탈출
            if index == len(nums):
                subset.pop()
                return
            
            # nums의 index 위치부터 마지막까지 재귀적으로 실행
            for i in range(index, len(nums)):
                dfs(i + 1, subset + [nums[i]])
                
        dfs(0, [])
        return answer
```

---

#### 알게된 점
  + 재귀구조는 계속 문제를 풀어야 익숙해짐

#### 어려웠던 점
  + 
