## 42. Trapping Rain Water

Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.

https://leetcode.com/problems/trapping-rain-water/

---


#### 풀이 1. max함수 이용
1. 리스트를 순회하며
2. m보다 높을 경우 -> 빗물 안고임
2-1. 뒤에 본인보다 높은게 없을 경우 -> m은 `height[i+1:]` 의 최대값
2-2. 뒤에 본인보다 높은게 있을 경우 -> 현재 높이가 m이 됨 
3. m보다 낮을 경우 -> 빗물 고임 
4. 전체에서 블럭이 차지하는 면적만큼 뺌

```python
class Solution(object):
    def trap(self, height):
        m = 0
        answer = 0
        for i, x in enumerate(height):
            if m <= x:
                answer += x
                if i + 1 < len(height) and max(height[i+1:]) <= x:
                    m = max(height[i+1:])
                else:
                    m = x
            else:
                answer += m
        
        return answer - sum(height)
```

Runtime : 시간초과 1  
Memory :   

답은 맞지만 최댓값을 매번 찾아야돼서 시간 복잡도 증가
뭔가 빙빙돌려서 푼듯 함

---

#### 풀이 2. 



```python





```



