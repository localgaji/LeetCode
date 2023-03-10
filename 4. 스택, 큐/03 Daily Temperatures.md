## 739. Daily Temperatures

Given an array of integers temperatures represents the daily temperatures, 
return an array answer such that answer[i] is the number of days you have to wait after the ith day to get a warmer temperature. 

If there is no future day for which this is possible, keep answer[i] == 0 instead.

https://leetcode.com/problems/daily-temperatures/description/


---

#### 풀이 1. 스택과 딕셔너리

1. 딕셔너리에 현재날짜:0 값 추가
3. 스택에 현재보다 온도가 낮은 값들을 제거하면서
4. 해당 날짜의 딕셔너리 값을 소요일(날짜 차이)로 변경
5. 스택에 (현재날짜, 온도) 추가
6. 딕셔너리 values 값들을 list로 반환

```python
class Solution(object):
    def dailyTemperatures(self, temperatures):

        dic, stack = {}, []

        for i, t in enumerate(temperatures):
            dic[i] = 0
            while stack and stack[-1][1] < t:
                day = stack.pop()[0]
                dic[day] = i - day
            stack.append((i,t))

        return list(dic.values())
```

메모리 사용 높음

---


#### 풀이 2. 딕셔너리 대신 리스트 활용

1. 리스트의 index가 key가 되는 딕셔너리는 만들 필요가 없음
2. 0이 n개 있는 리스트 생성하여 대체 가능

```python
class Solution(object):
    def dailyTemperatures(self, temperatures):

        dic = [0] * len(temperatures) #딕셔너리 대신 리스트
        stack = []

        for i, t in enumerate(temperatures):
            while stack and stack[-1][1] < t:
                day = stack.pop()[0]
                dic[day] = i - day
            stack.append((i,t))

        return dic
```

공간복잡도 개선
실행시간 개선
