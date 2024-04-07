125. Valid Palindrome
https://leetcode.com/problems/valid-palindrome/

1st   
結論：acceptされなかった/前処理で文字以外を削除するときに、誤って大文字アルファベットも削除していた   

●前処理   
文字を数値に変換するASCIIの関数があった気がするな   
アルファベットを数値に変更   
アルファベットの範囲以外の数値はすべて削除   

●アルゴリズム   
sの長さを2で割った商(half_len)の数だけ、回す(偶奇で場合わけ必要なくしている)   
while s <= half_lenは、前からの要素＝後ろからの要素が一致しているかどうか(一変数でいける)   
途中で一致していなかったら、false、回し切ったらtrue   

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        if len(s) <= 1:
            return True
        
        s_num = []
        
        for s_ in s:
            if ord('a') <= ord(s_) <= ord('z'): 
                s_num.append(ord(s_))
        
        half_len = len(s_num)//2
        j = 0
        
        while j <= half_len:
            if s_num[j] != s_num[-j-1]:
                return False
            j = j + 1
        
        return True
```


2nd   
1stの改善として、前処理で大文字を認識するようにする   
この問題の判定自体では大文字と小文字の区別をしないため、
大文字を小文字の数値に変換する    
あと数字も加味した  
ASCIIの一覧を見ながら+-を揃えた

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        if len(s) <= 0:
            return True
        
        s_num = []
        diff = ord('a') - ord('A')
        
        for s_ in s:
            if ord('a') <= ord(s_) <= ord('z') or ord('0') <= ord(s_) <= ord('9'): 
                s_num.append(ord(s_))
            elif ord('A') <= ord(s_) <= ord('Z'):
                s_num.append(ord(s_) + diff)
                
        
        half_len = len(s_num)//2
        j = 0
        
        while j <= half_len - 1:
            if s_num[j] != s_num[-j-1]:
                return False
            j = j + 1
        
        return True
```
