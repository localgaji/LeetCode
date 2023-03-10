## 24. Swap Nodes in Pairs

Given a linked list, swap every two adjacent nodes and return its head. 
You must solve the problem without modifying the values in the list's nodes 
(i.e., only nodes themselves may be changed.)

https://leetcode.com/problems/swap-nodes-in-pairs/

---

#### 풀이 1. 

`prev -> a1 (head) -> b1 -> a2 -> b2`

1. 연결리스트에서 a b 쌍을 스왑
2. b1 -> a1 를 연결, a1 -> a2 를 연결
3. prev -> b1 를 연결

`prev -> b1 -> a1 (head) -> a2 -> b2`

4. a2가 head, a1이 prev가 되도록 함

```python
class Solution(object):
    def swapPairs(self, head):

        answer = prev = ListNode(None)
        prev.next = head

        while head and head.next:
            b = head.next
            b.next, head.next = head, b.next
            prev.next = b

            prev = head
            head = head.next

        return answer.next
```

> Runtime : 91%  
Memory : 88%

