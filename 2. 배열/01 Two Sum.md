## 1. Two Sum

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

https://leetcode.com/problems/two-sum/

---

#### 풀이 1. for 이중 순회
1. for 문으로 리스트를 순회 (n)
2. for 문으로 해당 값 위치 이후의 리스트를 순회(m)하며 n+m 확인

```python
class Solution(object):
    def twoSum(self, nums, target):

        for i, n in enumerate(nums):
            for j, m in enumerate(nums[i+1:]):
                    if n + m == target:
                        return [i, i+j+1] 
```

> Runtime : 49.27%  
Memory : 98%

---

#### 풀이 2. 딕셔너리 이용
1. 딕셔너리 생성
2. for 문으로 리스트를 순회 (n)
3. `target - n` key가 딕셔너리에 있는지 확인
4. 있으면 리턴
5. 없으면 값(n) : 위치(i) 를 딕셔너리에 저장

```python
class Solution(object):
    def twoSum(self, nums, target):

        dic = {} # 값:인
        for i, n in enumerate(nums):
            if target - n in dic:
                return [i, dic[target - n]]  
            dic[n] = i
```

> Runtime : 71%  
Memory : 52%

딕셔너리 : 빠름
