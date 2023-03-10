## 92. Reverse Linked List II

Given the head of a singly linked list and two integers left and right where left <= right, 
reverse the nodes of the list from position left to position right, and return the reversed list.

https://leetcode.com/problems/reverse-linked-list-ii/

---

#### 풀이 1. 

1. 

```python
class Solution(object):
    def reverseBetween(self, head, left, right):

        answer = before = ListNode(None)
        before.next = head
        index, count = 0, 0

        while before and head and count < right - left:
            index += 1
            if index >= left:
                start = before.next
                head.next.next, before.next, head.next = start, head.next, head.next.next
                count += 1

            elif index < right:
                head = head.next
                before = before.next

        return answer.next
```

> Runtime : 15 ~ 97%  
Memory : 40%

