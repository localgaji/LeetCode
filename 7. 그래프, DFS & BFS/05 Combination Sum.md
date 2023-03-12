## 39. Combination Sum

Given an array of distinct integers candidates and a target integer target,  
return a list of all unique combinations of candidates where the chosen numbers sum to target.  
You may return the combinations in any order.

The same number may be chosen from candidates an unlimited number of times.  
Two combinations are unique if the frequency of at least one of the chosen numbers is different.

The test cases are generated such that the number of unique combinations that sum up to target is less than 150 combinations for the given input.

https://leetcode.com/problems/combination-sum/

---

#### 풀이 1. DFS

```python
def CombinationSum(candidates, target):
    result = []
    def dps(csum, index, path):

        if csum <=0:
            if csum == 0:
                result.append(path)
            return

        for i in range(index, len(candidates)):
            dps(csum - candidates[i], i, path + [candidates[i]])

    dps(target, 0, [])

    return result
```

---

#### 알게된 점
  + 

#### 어려웠던 점
  + 2-2-2-2 > 7 이므로, 2-2-2-3, 2-2-2-6 등은 탐색할 필요가 없으나 이 풀이에서는 탐색 하였다. 불필요한 과정을 스킵하기 위해서는 어떻게 해야할지?
