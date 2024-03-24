242. Valid Anagram   
https://leetcode.com/problems/valid-anagram/

0:自力でやった結果、大体の方針は立つがコードが書けない。。    
方針1としては、      
・文字を数字に変換   
・並び変える   
・一つのloopでs・tを同時に左から順にみて、ひとつでも異なっていたら、false   
・問題なく回しきれたらtrue   

方針2としては、    
・sでハッシュテーブルを作る      
　・文字と出現回数   
・tの文字が出てきた回数だけ、上記ハッシュテーブルから引き算をする   
　・(仕様がわからないので)引き算した結果がマイナスもしくは引けなくなったら、false   
・回し切れたらtrue   
→ハッシュテーブルを作る文法が思い出せない   

1st   
以下のURLのアプローチ2を参考にして、      
sの文字と出現頻度でハッシュテーブルを作って、tで左記ハッシュテーブルを削除後、   
残ったハッシュテーブルのvalのリストから0ではない値が一つでもあればFalse、問題なく回しきればTrue   

参考にした解答   
https://leetcode.com/problems/valid-anagram/discuss/3687854/3-Method's-oror-C%2B%2B-oror-JAVA-oror-PYTHON-oror-Beginner-Friendly   

defaultdictは以下の公式ドキュメントを確認   
https://docs.python.org/ja/3/library/collections.html#collections.defaultdict   

dictのloop(.values()等)について公式ドキュメントで確認   
https://docs.python.org/ja/3/library/stdtypes.html#dict-views   


```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        
        count = defaultdict(int)
        
        for x in s:
            count[x] += 1
        for x in t:
            count[x] -= 1
            
        for val in count.values():
            if val != 0:
                return False
        return True

```

2nd:林さんのコメントをもとに1stを改善   
・xをcに
・tによるハッシュテーブル削除の際にすでに0だったら、falseにした
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        
        count = defaultdict(int)
        
        for c in s:
            count[c] += 1
        for c in t:
            if count[c] == 0:
                return False
            count[c] -= 1
            
        for val in count.values():
            if val != 0:
                return False
        return True

```

3rd?:sortでの解きなおし   
方針：   
・関数を作成：strをリストに変換して、リスト内の文字を昇順に変更、文字列にして返す   
(sとtで同じ処理を二回やるのが面倒だと思ったので、関数化しようと思いついた)      
・s・tを上記関数で変換   
・sとtが一致していたら、True/それ以外はFalse
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        def str_sort(c):
            temp = list(c)
            temp = sorted(temp)
            c = str(temp)
            return c

        s = str_sort(s)
        t = str_sort(t)

        if s == t:
            return True
        else:
            return False



```
