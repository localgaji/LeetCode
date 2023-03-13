## 819. Most Common Word

Given a string paragraph and a string array of the banned words banned, return the most frequent word that is not banned. It is guaranteed there is at least one word that is not banned, and that the answer is unique.

The words in paragraph are case-insensitive and the answer should be returned in lowercase.

https://leetcode.com/problems/most-common-word/

---


#### 풀이 1. 딕셔너리 이용
1. 특수기호를 공백으로 변경 - 정규표현식 re.sub
2. self.split() 이용하여 단어 리스트 words 생성
3. defaultdict 으로 value 기본값이 int인 딕셔너리 생성
4. for문으로 words 리스트 순회하며 단어가 banned에 없을 경우 해당 단어 key의 value 값에 1 추가  
5. max`함수로 values 중 최대값을 얻기
6. 딕셔너리.items()로 딕셔너리를 순회하며 최대값 values를 가진 key를 찾아서 리턴

```python
class Solution(object):
    def mostCommonWord(self, paragraph, banned):

        dic = defaultdict(int)
        clean = re.sub(r'[^a-z]', " ", paragraph.lower())
        words = clean.split()

        for word in words:
            if word and (not word in banned):
                dic[word] += 1
        
        m = max(dic.values())
        for key, value in dic.items():
            if value == m:
                return key
```

+ 딕셔너리.items() : (key, value) 튜플로 구성된 list를 반환

> Runtime : 75.58%  
Memory : 89.53%

max로 values를 한번 순회한 후  
items()으로 또 순회하여 비효율적임 

---

#### 풀이 2. Counter 함수
1. 특수기호를 공백으로 변경 - 정규표현식 re.sub
2. self.split() 이용하여 단어 리스트 생성 & 리스트내포로 banned 제거
4. Counter(데이터) 함수로 데이터에 각 원소가 몇 개 있는지 저장된 딕셔너리를 반환  
5. most_common 메서드로 최빈값 리턴

```python
class Solution(object):
    def mostCommonWord(self, paragraph, banned):

        clean = re.sub(r'[^a-z]', " ", paragraph.lower())
        words = [w for w in clean.split() if not w in banned]
        count = Counter(words)

        return count.most_common(1)[0][0]
```

+ Counter(데이터) : 데이터에 각 원소가 몇 개 있는지 저장된 딕셔너리를 반환  
+ 카운터객체.most_common(k) : 가장 많이 등장하는 key k개를 (key, value) 쌍 리스트로 반환  
  ex) `[(key1, value1), (key2, value2), ... ]`

> Runtime : 39.53%  
Memory : 41.28%



