## 121. Best Time to Buy and Sell Stock

You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

---

#### 풀이 1. 지금까지의 최소 가격, 지금까지의 최대 수익을 변수에 저장

1. 지금까지의 최소 가격 `min_price`, 지금 시점에서 최대 수익 `max_profit`
2. for 순회하며 지금까지의 최소 가격과 현재 가격을 비교한다.
3. 현재 가격이 min_price보다 더 낮을 경우, 현재 가격을 min_price에 저장한다
4. 현재 시점에서 최대 수익을 계산한다
5. 현재 최대 수익이 기존 최대 수익보다 높을 경우, 현재 최대수익을 max_profit에 저장한다.
6. max_profit을 리턴

```python
class Solution(object):
    def maxProfit(self, prices):
        min_price = 10000
        max_profit = 0
        for x in prices:
            if x < min_price:
                min_price = x

            profit = x - min_price

            if profit > max_profit: 
                max_profit = profit

        return max_profit
```

> Runtime : 92.93%  
Memory : 15.90%

---
