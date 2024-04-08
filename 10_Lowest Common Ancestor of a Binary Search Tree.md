235. Lowest Common Ancestor of a Binary Search Tree   
https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/

0:BSTの知識不足と問題の論理が難しかった   
方針:   
操作としては、p・qのノードから上のノードにたどって、   
初めて合流したときのノードがアウトプット   
ただ上のノードをどのようにたどるかがわからない      

1st   
以下の解答を参考にしました   
方針：rootから初めて、LCAでなければ進めて、止まったらLCAを返す(値の条件をうまく使う)
・LCAの条件は2パターン
　・LCAがp・qどちらかのパターン
　・LCAがp・qの共通の親
・なので、LCAではない条件は以下となる
　・LCA候補が<p,q or >p,q

https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/discuss/4276179/Beats-99-or-O(-log(n))-or-(Step-by-step-explanation)   

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        
        while root:
            if root.val > p.val and root.val > q.val:
                root = root.left
            elif root.val < p.val and root.val < q.val:
                root = root.right
            else:
                return root
```


