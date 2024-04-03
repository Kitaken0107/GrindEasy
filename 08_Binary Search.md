704. Binary Search
https://leetcode.com/problems/binary-search/

0:自力でやり、binary searchがうる覚えで頓挫しました   
全探索 or binary search   
並んであることを活かす   
リストの長さを2で割った商の数を左側・残りを右側にする   
target　< 左側リストの一番右の数→左側を再度分割
(右も同様)
indexをアウトプットするにはどうしたらよいのだ？となった

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        def binary_search(num_list):
            if len(num_list) == 1:
                return  
            base = num_list//2
            if target == num_list[base]:
                return 
            elif target < num_list[base]:
                binary_search(num_list[:base])
            elif
                binary_search(num_list[base:])


```


1st   
以下の解答を参考にしました   
https://leetcode.com/problems/binary-search/discuss/2700642/Python-Classic-Binary-Search-Problem-or-99-Faster-or-Fastest-Solution   

5分内に再現できるようにしました   
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left = 0
        right = len(nums)-1
        
        while left <= right:
            mid = (left + right)//2
            
            if nums[mid] == target:
                return mid
            elif nums[mid] > target:
                right = mid - 1
            else:
                left = mid + 1
        return -1

```


