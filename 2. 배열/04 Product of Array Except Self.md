## 238. Product of Array Except Self

Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].

The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

You must write an algorithm that runs in O(n) time and without using the division operation.

https://leetcode.com/problems/product-of-array-except-self/

---


#### 풀이 1. 
```
[  a    b    c    d  ]   
   1    a   ab   abc    정방향으로 곱한 리스트
  bcd   dc   d    1     역방향으로 곱한 리스트
 
[ bcd  adc  abd  abc ]  두 리스트 요소를 곱한 리스트
```

```python
class Solution(object):
    def productExceptSelf(self, nums):
        time = 1
        forward = []
        for i in range(0, len(nums)):
            forward.append(time)
            time *= nums[i]
        
        time = 1
        answer = []
        for j in range(len(nums)-1, -1, -1):
            answer.append(time * forward[j])
            time *= nums[j]

        return reversed(answer)
```

> Runtime : 44.32%  
Memory : 31.66%

answer리스트를 생성하고 다시 뒤집는 과정이 비효율적이다  
for문의 순서를 변경하면 방향이 맞지 않음

---

#### 풀이 2. (개선) 새 리스트 생성 없이 forward 리스트의 요소를 변경

```python
class Solution(object):
    def productExceptSelf(self, nums):
        time = 1
        forward = []
        for i in range(0, len(nums)):
            forward.append(time)
            time *= nums[i]
        
        time = 1
        for j in range(len(nums)-1, -1, -1):
            forward[j] =  time * forward[j]
            time *= nums[j]

        return forward
```

> Runtime : 84.63%  
Memory : 80.36%

* 쉽지만 잘 안써지는 기능 `list[i] = x` 
