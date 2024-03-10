leetcode two sum   
https://leetcode.com/problems/two-sum/   

1st   
i,jの2変数でブルートフォース   
愚直な方法で実装

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
    
        for i in range(len(nums)):
            for j in range(i+1,len(nums),1):
                if target == nums[i] + nums[j]:
                    return [i,j]
                    break
```

2nd   
別解を参考にハッシュテーブルで実装      
O(1)で検索できるのがよいっぽい・空間はO(n)を使う

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        table = {}
        for i in range(len(nums)):
            table[nums[i]] = i
        for i in range(len(nums)):
            sub = target - nums[i]
            if sub in table and table[sub] != i:
                return [i,table[sub]]
```
