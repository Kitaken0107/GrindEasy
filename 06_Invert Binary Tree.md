226. Invert Binary Tree   
https://leetcode.com/problems/invert-binary-tree/   

1st   
結論   
TreeNodeのデータ構造ではなく、リストみたいに扱ってしまったため、途中で放棄しました   
方針   
各深さごとのノードを、一時的にstackにデータを入れて、stackの値をtreeに再度逆から代入   

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

import math
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        depth = 0
        width = 0
        temp_stack = []
        
        while depth <= math.log2(len(root)+1):
            while width <= (depth-1)**2:
                temp_stack.append(root[ + width])
                width += 1
            width = 0
            while width <= (depth-1)**2:
                root[ + width] = temp_stack.pop()
                width +=1
            width = 0
        
        return root
```


2nd   
解答を見る   
recursive   
何も見ずに3回再現   
https://leetcode.com/problems/invert-binary-tree/discuss/2463600/Easy-oror-100-oror-Fully-Explained-oror-Java-C%2B%2B-Python-JS-C-Python3-oror-Recursive-and-Iterative   
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        
        if root == None:
            return root
        
        temp = root.left
        root.left = root.right
        root.right = temp
        
        self.invertTree(root.left)
        self.invertTree(root.right)
        
        return root
```
