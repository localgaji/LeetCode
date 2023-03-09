## 125. Valid Palindrome

A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. 
Alphanumeric characters include letters and numbers.

Given a string `s` , return `true` if it is a palindrome, or `false` otherwise.

---


#### 풀이 1. 정규표현식  
1. 정규표현식으로 공백 제거 / 대문자를 소문자로 변경
2. for문으로 양끝부터 중앙까지 탐색

```
import re
class Solution(object):
    def isPalindrome(self, s):
        answer = True
        a = re.sub(r"[^a-z0-9]", "", s.lower())
        
        for n in range(0,int(len(a)/2)):
            if a[n] != a[len(a)-n-1]:
                return False

        return answer
```

Runtime : 31 ms / 84.72%  
Memory : 16.3 MB / 12.60%

---

#### 풀이 2. isalnum 함수
1. isalnum 함수 사용하여 문자 판별
2. for 문으로 대문자를 소문자로 변경 
3. 문자를 리스트에 담기
4. for 문으로 양끝부터 중앙까지 탐색

```
class Solution(object):
    def isPalindrome(self, s):
        answer = True
        a = []
        for i in s:
            if i.isalnum():
                a.append(i.lower())
        
        for n in range(0,int(len(a)/2)):
            if a[n] != a[len(a)-n-1]:
                return False

        return answer
```

Runtime : 39 ms / 62.24 %  
Memory : 15.9 MB / 18.50 %

정규표현식에 비해 살짝 느린 속도

---

#### 풀이 3. 문자열 슬라이싱  
1. 정규표현식으로 공백 제거 / 대문자를 소문자로 변경
2. 문자열 슬라이싱 `[::-1]` : 문자열을 뒤집음

```
class Solution(object):
    def isPalindrome(self, s):
        import re
        a = re.sub(r"[^a-z0-9]", "", s.lower())
        
        if a != a[::-1]:
            return False 

        return True
```

Runtime : 24 ms / 95.97%  
Memory : 16.3 MB / 12.60%

문자열 슬라이싱 기능 : 파이썬 자체에서 효율적으로 구현되어있어 순회문보다 시간이 단축됨

---

