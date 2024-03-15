121. Best Time to Buy and Sell Stock   
https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

1st    
総当たりでやる   
解答見ずに実施   
時間計算量O(n**2)       
空間計算量O(1)    
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        max_profit = 0
        for i in range(len(prices)):
            for j in range(i+1,len(prices)):
                profit = prices[j]-prices[i]
                max_profit = max(profit,max_profit)        
        return max_profit
```

2nd   
解答を見た   
時間計算量O(n)   
sell・buyを二つ用意して、sellを動かす際に、buy<sellだったら、過去のprofitとmaxで比較、buy>=sellだったら、最小のbuyとして更新する   
参考：https://leetcode.com/problems/best-time-to-buy-and-sell-stock/discuss/4845631/VIDEO-Intuitive-Visualization-and-Proof-of-O(n)-Solution   

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        profit = 0
        buy = prices[0]
        sell = prices[1]
        for sell in prices[1:]:
            if sell > buy:
                profit = max(profit,sell-buy)
            else:
                buy = sell
        return profit
```
