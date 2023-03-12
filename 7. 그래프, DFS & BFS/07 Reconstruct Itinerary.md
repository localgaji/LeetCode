## 332. Reconstruct Itinerary

You are given a list of airline tickets where `tickets[i] = [fromi, toi]` represent the departure and the arrival airports of one flight. 
Reconstruct the itinerary in order and return it.

All of the tickets belong to a man who departs from `"JFK"`, thus, the itinerary must begin with `"JFK"`. 
If there are multiple valid itineraries, you should return the itinerary that has the smallest lexical order when read as a single string.

For example, the itinerary `["JFK", "LGA"]` has a smaller lexical order than `["JFK", "LGB"]`.  
You may assume all tickets form at least one valid itinerary. You must use all the tickets once and only once.

https://leetcode.com/problems/reconstruct-itinerary

---

#### 풀이 1. DFS 재귀 구조
1. 출발 : 목적지 딕셔너리 `graph`를 생성
2. 
3.
4.


```python
class Solution(object):
    def findItinerary(self, tickets):
        answer = []
        
        # graph 생성
        graph = collections.defaultdict(list)
        for route in sorted(tickets, reverse=True):
            graph[route[0]] += [route[1]]
        
        # 재귀 구조 : 
        def dfs(dep):
            while dic[dep]:
                arr = graph[dep].pop()
                dfs(arr)
            answer.append(dep)

        dfs("JFK")
        return answer[::-1] #마지막 목적지부터 담았으므로 뒤집어줌
```

---

#### 알게된 점
  + 

#### 어려웠던 점
  + 
