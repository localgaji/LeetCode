## 21. Merge Two Sorted Lists

You are given the heads of two sorted linked lists list1 and list2.

Merge the two lists in a one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.

https://leetcode.com/problems/merge-two-sorted-lists/

---

#### 풀이 1. 

1. 두 연결리스트 중 head의 값이 작은 연결리스트를 list1으로 지정한다.
2. answer 연결 리스트를 생성, answer의 head를 list1 헤드로 연결한다.
3. list1이 list2보다 작을 때까지 list1을 앞으로 이동
4. list1 연결리스트를 list2보다 작은부분 / 큰부분으로 자름
5. 작은부분은 list2와 연결함 (list1작 -> list2)
6. 큰부분은 list1이 됨 
7. list1과 list2를 서로 바꿔서 list1 값이 작도록 함
8. list1 또는 list2가 없어지면 모두 한 리스트로 연결된 것이므로 answer 리스트를 리턴한다. 


```python
class Solution(object):
    def mergeTwoLists(self, list1, list2):

        if not list1:
            return list2
        if not list2:
            return list1
        
        if list1.val > list2.val:
            list1, list2 = list2, list1
            
        answer = ListNode(0)
        answer.next = head = list1

        while list1 and list2:
            while list1.next and list1.next.val < list2.val:
                list1 = list1.next
            list1.next, list1 = list2, list1.next
            list1, list2 = list2, list1

        return answer.next
```

> Runtime : 35.18%  
Memory : 14.5%  

---
