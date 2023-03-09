## 49. Group Anagrams

Given an array of strings `strs`, group the anagrams together. You can return the answer in any order.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

https://leetcode.com/problems/group-anagrams/

---


#### 풀이 1. 딕셔너리 이용
1. for 문으로 리스트 `s`의 요소들을 한개의 문자열 `s_sorted` 로 합치기
2. 딕셔너리에 `s_sorted` : [... , s] 추가

```python
class Solution(object):
    def groupAnagrams(self, strs):
    
        anagram_dict = {}
        for s in strs:
            s_sorted = "".join(sorted(s)) #주의1
            if s_sorted in anagram_dict: #주의2
                anagram_dict[s_sorted].append(s)
            else:
                anagram_dict[s_sorted] = [s]

        return list(anagram_dict.values()) #주의3
```

Runtime : 65%  
Memory : 76%

* 주의1 : `sorted(a)` 함수는 문자열에도 사용 가능
* 주의2 : 딕셔너리의 key를 순회할 때 `dic.keys()` 를 형성하여 순회하면 시간이 매우 많이 소요됨  
  그냥 `for key in dic` 순회 가능
* 주의3 : `dic.keys()`와 `dic.values()`의 자료형은 리스트가 아님  
  `dict[a, ... ]` 로 출력

---

