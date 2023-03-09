## 937. Reorder Data in Log Files

You are given an array of `logs`. Each log is a space-delimited string of words, where the first word is the identifier.

There are two types of logs:

Letter-logs: All words (except the identifier) consist of lowercase English letters.
Digit-logs: All words (except the identifier) consist of digits.
Reorder these logs so that:

The letter-logs come before all digit-logs.
The letter-logs are sorted lexicographically by their contents. If their contents are the same, then sort them lexicographically by their identifiers.
The digit-logs maintain their relative ordering.
Return the final order of the logs.

https://leetcode.com/submissions/detail/906658788/

---


#### 풀이 1. lambda를 이용한 정렬
1. `for` 문을 이용하여 `logs` 탐색
2. `split()` 함수를 이용하여 `log` 속 word 각각을 리스트의 요소로 변환
3. 리스트 두번째 항목을 검사하여 문자열/숫자 여부 판단
4. `digit` / `letter` 리스트에 추가하기
5. letter 리스트 내부를 정렬 : `sort()` 함수의 lambda key 사용
    * lambda key 에 튜플 입력시 요소 순차대로 적용  
          `a.sort( key = lambda x : (x[1], x[2]) ) `
    * lambda key가 list일 경우 : 요소 순차대로 정렬 기준이 됨  
          `a.sort(key = lambda x : L1[1:]) `
6. letter와 digit를 합쳐 return

```
class Solution(object):
    def reorderLogFiles(self, logs):

        digit, letter = [], []
        
        for log in logs:
            if log.split()[1].isdigit():
                digit.append(log)
            else:
                letter.append(log)
        
        letter.sort(key=lambda x : (x.split()[1:], x.split()[0]))

        return letter + digit
```

Runtime : 24 ms / 61.36%  
Memory : 14.1 MB / 81.82%

---

