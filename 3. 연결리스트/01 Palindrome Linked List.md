## 234. Palindrome Linked List

Given the head of a singly linked list, return true if it is a 
palindrome or false otherwise.

https://leetcode.com/problems/palindrome-linked-list/

---

#### 풀이 1. Runner 방법

연결리스트의 길이는 끝까지 순회하지 않으면 알 수 없음  

1. fast 런너로 두칸씩 이동하며 순회하고
동시에 slow 런너로 한칸씩 순회하며 
역방향 연결리스트 rev를 생성한다
2. slow가 연결리스트의 중간 지점에 왔을 때 순회를 멈춘다
3. rev 연결 리스트와 slow 연결 리스트를 순회하며 값이 같은지 확인한다.

```python
class Solution(object):
    def isPalindrome(self, head):
        rev = None
        fast, slow = head, head

        while fast and fast.next:
            fast = fast.next.next
            now = slow
            rev, rev.next, slow = now, rev, slow.next

        if fast: #요소 개수가 홀수일때 slow를 다음칸으로 넘김
            slow = slow.next 
        
        while rev and slow.val == rev.val:
            slow = slow.next
            rev = rev.next

        return not rev
```

> Runtime : 96.37%  
Memory : 99.21%

