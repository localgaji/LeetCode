## 2. Add Two Numbers

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

https://leetcode.com/problems/add-two-numbers/

---

#### 풀이 1. 

1. answer 연결리스트 생성
2. carried와 l1과 l2를 더한 값 val
3. val이 10이 넘을 경우, 다음 자리로 1을 이월하고 val에는 일의자리만 남김
4. 10이 안넘으면 이월값은 0임
5. answer 연결리스트에 val을 추가

```python
class Solution(object):
    def addTwoNumbers(self, l1, l2):

        answer = head = ListNode(0)
        carried = 0
        while l1 or l2:
            val = carried

            if l1:
                val += l1.val
                l1 = l1.next
            if l2:
                val += l2.val
                l2 = l2.next

            if val >= 10:
                carried = 1
                val -= 10
            else:
                carried = 0
            
            head.next = ListNode(val)
            head = head.next

        if carried == 1:
            head.next = ListNode(1)

        return answer.next
```

> Runtime : 30 ~ 93%  
Memory : 21 ~ 93%

