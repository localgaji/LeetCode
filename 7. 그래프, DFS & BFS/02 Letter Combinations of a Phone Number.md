## 17. Letter Combinations of a Phone Number

Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. 
Return the answer in any order.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

https://leetcode.com/problems/letter-combinations-of-a-phone-number/

---

#### 풀이 1. 이중 for문

```python
class Solution(object):
    def letterCombinations(self, digits):

        dic = {"2":"abc", "3":"def", "4":"ghi", "5":"jkl", 
            "6":"mno", "7":"pqrs", "8":"tuv", "9":"wxyz"} 
            
        answer = []
        
        
        for n in digits:
            if not answer:
                answer = [""] 
                
            divisor = len(answer) 
            answer *= len(dic[n]) # answer 리스트를 dic[n]배 반복
            
            # 늘어난 answer 리스트에 dic[n] 문자들을 위치에 맞게 추가하기
            for index in range(0, len(answer)):
                answer[index] += dic[n][index // divisor]

        return answer      
```

---

#### 풀이2. DFS

```python

```
