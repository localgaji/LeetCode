## 344. Reverse String

Write a function that reverses a string. The input string is given as an array of characters `s`.

You must do this by modifying the input array in-place with `O(1)` extra memory.

https://leetcode.com/problems/reverse-string/description/

---
#### 풀이1. 투 포인터 이용

1. x는 리스트의 맨앞, y를 맨뒤를 가리키도록 설정
2. 중앙으로 이동하며 x위치의 값과 y위치의 값을 서로 바꾸기

```
class Solution(object):
    def reverseString(self, s):

        x, y = 0, len(s) - 1 

        while x < y:
            s[x], s[y] = s[y], s[x] 
            x += 1
            y -= 1
        return s  
```

Runtime : 148 ms / 85.29%  
Memory : 20.9 MB / 96.16%

---

#### 풀이2. 파이썬 내장함수 self.reverse()

```
class Solution(object):
    def reverseString(self, s):
        return s.reverse()
```

Runtime : 149 ms / 83.5% 
Memory : 21.1 MB / 82.49%

과정을 떠올릴 필요가 없어 간단하다.

---

