## 347. Top K Frequent Elements

Given an integer array nums and an integer k, return the k most frequent elements. You may return the answer in any order.

https://leetcode.com/problems/top-k-frequent-elements

---

#### 풀이 1. Counter 모듈로 개수 딕셔너리 자동생성

```python
class Solution(object):
    def topKFrequent(self, nums, k):

        count = Counter(nums)
        items = list(count.items())
        items.sort(key=lambda x : x[1])

        return [i for i, j in items[-k:]]
```

---

#### 풀이 2. Counter 모듈의 most_common 메서드

```python
class Solution(object):
    def topKFrequent(self, nums, k):
        return [x for x, n in Counter(nums).most_common(k)]
```

+ `Counter(list).most_common(k)` : 가장 자주 등장하는값 k개를 key, value 튜플로 반환
