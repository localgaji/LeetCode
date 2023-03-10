## 328. Odd Even Linked List

Given the head of a singly linked list, group all the nodes with odd indices together followed by the nodes with even indices, and return the reordered list.

The first node is considered odd, and the second node is even, and so on.

Note that the relative order inside both the even and odd groups should remain as it was in the input.

You must solve the problem in O(1) extra space complexity and O(n) time complexity.

https://leetcode.com/problems/odd-even-linked-list/

---

#### 풀이 1. 

1. answer 연결리스트 생성
2. last_odd는 가장 가까운 홀수번째 노드임, 먼저 첫번째 노드를 가리킴  
answer : `last_odd -> first_even (head) -> next_odd (head.next) -> next_odd.next`  
3. `last_odd -> next_odd -> first_even (head) -> next_odd.next`  
4. `next_odd (last_odd) -> first_even -> next_odd.next (head)`  

```python
class Solution(object):
    def oddEvenList(self, head):

        answer = last_odd = head
        if not head or not last_odd.next :
            return answer
        head = last_odd.next 

        while last_odd and head and head.next:
            next_odd = head.next
            first_even = last_odd.next
            
            last_odd.next, next_odd.next, head.next = next_odd, first_even, next_odd.next

            last_odd = last_odd.next
            head = head.next

        return answer
```

> Runtime : 68 ~ 76%  
Memory : 13 ~ 99%

