## 316. Remove Duplicate Letters

Given a string s, remove duplicate letters so that every letter appears once and only once. You must make sure your result is 
the smallest in lexicographical order
 among all possible results.

https://leetcode.com/problems/remove-duplicate-letters/

---

#### 풀이 1. 스택

1. 

```python
class Solution(object):
    def removeDuplicateLetters(self, s):

        counter = Counter(s)
        stack = []

        for i in s:
            counter[i] -= 1
            if not i in stack:
                while stack and stack[-1] > i and counter[stack[-1]] > 0:
                    stack.pop()
                stack.append(i)

        return "".join(stack)
```

스택 개념은 알겠으나 
힌트를 안보고 어떻게 바로 스택을 떠올릴수 있을지 . . .
