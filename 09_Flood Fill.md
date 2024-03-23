733. Flood Fill   
https://leetcode.com/problems/flood-fill/

0:自力でやってできなかった      
方針：   
recursiveでできる気がする   
上左右下の順に判定する   
・自分と同一の値ではない・値がない・すでに探索済み→何もしない
・自分と同一の値だったら、colorを代入   
recursiveの関数の設定で分からなくなりました
 
```python
class Solution:
    def floodFill(self, image: List[List[int]], sr: int, sc: int, color: int) -> List[List[int]]:
        
    max_r = len(image) -1
    max_c = len(image[0]) - 1

    def 
 

        return 
```


1st   
recursive   
以下を参考に実施　　　
https://leetcode.com/problems/flood-fill/discuss/1772478/Python-3-(150ms)-or-Clean-DFS-Solution-or-Easy-to-Understand　　　   
   
5分以内でできるようにしました
```python
class Solution:
    def floodFill(self, image: List[List[int]], sr: int, sc: int, newColor: int) -> List[List[int]]:
        row = len(image)
        col = len(image[0])
        same_value = image[sr][sc]
        
        def dfs(r,c):
            if r<0 or r > row-1 or c<0 or c > col -1 or image[r][c] != same_value or image[r][c] == newColor:
                return
            
            image[r][c] = newColor
            dfs(r+1,c)
            dfs(r-1,c)
            dfs(r,c+1)
            dfs(r,c-1)
            
        dfs(sr,sc)
        
        return image
```

2~3:5分くらいで書いて、サンプルケースをイメージして確認
```python
class Solution:
    def floodFill(self, image: List[List[int]], sr: int, sc: int, newColor: int) -> List[List[int]]:
        max_row = len(image)
        max_col = len(image[0])
        same_value = image[sr][sc]
        
        def dfs(r,c):
            if  r<0 or r> max_row-1 or c < 0 or c > max_col - 1 or image[r][c] != same_value or image[r][c] == newColor:
                return
            
            image[r][c] = newColor
            dfs(r+1,c)
            dfs(r-1,c)
            dfs(r,c+1)
            dfs(r,c-1)
        
        dfs(sr,sc)
        
        return image
```

