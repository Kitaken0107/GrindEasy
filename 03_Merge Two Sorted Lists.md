21. Merge Two Sorted Lists   
https://leetcode.com/problems/merge-two-sorted-lists/

1st   
回らない   
以下書きながら悩んだ気がします   
・dummyを使う記憶はあったが、returnでdummyにするか、dummy.mextにするかどっちだろう   
・何も見ずに解こうとすると、「接続先を変える」・「ノードを一つ先を進める」のそれぞれの操作が、何に何を代入するか、=の左辺・右辺どっちにするか、いつもこんがらがる   
・ListNode(list1)をしたのはなぜか思い出せないのですが、classの理解が怪しいのかもしれません
   
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        dummy = ListNode()
        list1 = ListNode(list1)
        list2 = ListNode(list2)
        if list1 is None and list2 is None:
            return []
        while list1 or list2:
            if list2 is None or list1.val <= list2.val:
                list1 = dummy.next
                list1 = list1.next
                dummy.next = dummy
            else:
                list2 = dummy.next
                list2 = list2.next
                dummy.next = dummy               
        return dummy

```

2nd   
ここで一回答えを少し見ました   
dummyとcurがそれぞれ必要で、curを動かすという考えを踏襲して書いてみました   

time exceedと出力   
変なところとして 以下の順序を逆にしないとcurがlist1の元の値を飛ばしてしまうことにあとから気づきました   
list1 = list1.next   
cur = list1


```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        cur = dummy = ListNode()
        
        while list1 and list2:
            if list1.val <= list2.val:
                cur.next =list1
                list1 = list1.next
                cur = list1
            else:
                cur.next =list2
                list2 = list2.next
                cur = list2
        if list1:
            cur.next = list1
        elif list2:
            cur.next = list2
        return dummy.next
```

3rd
再度書き直し
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        cur = dummy = ListNode()
        while list1 and list2:               
            if list1.val < list2.val:
                cur.next = list1
                cur = list1
                list1 = list1.next
            else:
                cur.next = list2
                cur = list2
                list2 = list2.next
                
        if list1:
            cur.next = list1
        elif list2:
            cur.next = list2
        
        return dummy.next
```
21. Merge Two Sorted Lists   
https://leetcode.com/problems/merge-two-sorted-lists/

1st   
回らない   
以下書きながら悩んだ気がします   
・dummyを使う記憶はあったが、returnでdummyにするか、dummy.mextにするかどっちだろう   
・何も見ずに解こうとすると、「接続先を変える」・「ノードを一つ先を進める」のそれぞれの操作が、何に何を代入するか、=の左辺・右辺どっちにするか、いつもこんがらがる   
・ListNode(list1)をしたのはなぜか思い出せないのですが、classの理解が怪しいのかもしれません
   
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        dummy = ListNode()
        list1 = ListNode(list1)
        list2 = ListNode(list2)
        if list1 is None and list2 is None:
            return []
        while list1 or list2:
            if list2 is None or list1.val <= list2.val:
                list1 = dummy.next
                list1 = list1.next
                dummy.next = dummy
            else:
                list2 = dummy.next
                list2 = list2.next
                dummy.next = dummy               
        return dummy

```

2nd   
ここで一回答えを少し見ました   
dummyとcurがそれぞれ必要で、curを動かすという考えを踏襲して書いてみました   

time exceedと出力   
変なところとして 以下の順序を逆にしないとcurがlist1の元の値を飛ばしてしまうことにあとから気づきました   
list1 = list1.next   
cur = list1


```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        cur = dummy = ListNode()
        
        while list1 and list2:
            if list1.val <= list2.val:
                cur.next =list1
                list1 = list1.next
                cur = list1
            else:
                cur.next =list2
                list2 = list2.next
                cur = list2
        if list1:
            cur.next = list1
        elif list2:
            cur.next = list2
        return dummy.next
```

3rd
再度書き直し
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        cur = dummy = ListNode()
        while list1 and list2:               
            if list1.val < list2.val:
                cur.next = list1
                cur = list1
                list1 = list1.next
            else:
                cur.next = list2
                cur = list2
                list2 = list2.next
                
        if list1:
            cur.next = list1
        elif list2:
            cur.next = list2
        
        return dummy.next
```
