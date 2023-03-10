## 20. Valid Parentheses

Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.

https://leetcode.com/problems/valid-parentheses/description/

---

#### 풀이 1. 스택

1. 열린괄호 -> 스택에 추가
2. 닫힌괄호 -> 스택을 pop, 딕셔너리에 연결된 value(열린 괄호)가 pop한 값과 같은지 검사
3. 스택이 남아있는지 검사

```python
class Solution(object):
    def isValid(self, s):

        stack = []
        dic = { ")":"(", "]":"[", "}":"{" }

        for i in s:
            if i in dic.values():
                stack.append(i)
            else:
                if not stack or dic[i] != stack.pop():
                    return False
            
        if stack:
            return False
            
        return True
```


