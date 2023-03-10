## 206. Reverse Linked List

Given the head of a singly linked list, reverse the list, and return the reversed list.

https://leetcode.com/problems/reverse-linked-list/

---

연결리스트를 뒤집는 문제
rev 연결리스트를 만들어서 역순으로 연결해준다

#### 풀이 1. 

1. 순회할 연결리스트 node
2. 역방향으로 저장할 연결리스트 rev
3. node를 순회하면서 rev 생성

```python
class Solution(object):
    def reverseList(self, head):

        node = head
        rev = None
        while node:
            rev, rev.next, node = node, rev, node.next 
        
        return rev
```

> Runtime : 66%  
Memory : 33~99%

다중할당을 하지 않으면  
rev가 node를 참조하므로 
rev.next는 node.next와 같은 값을 참조하고
node.next는 rev를 가리키게 된다

