```go
type Trie struct {
	IsEnd bool
	Next  [26]*Trie
}

/** Initialize your data structure here. */
func Constructor2() Trie {
	return Trie{
		IsEnd: false,
		Next: [26]*Trie{},
	}
}

/** Inserts a word into the trie. */
func (this *Trie) Insert(word string)  {
	if word == "" || len(word) == 0 {
		return
	}
	for i := 0 ; i < len(word) ; i ++ {
		n := word[i] - 'a'
		if this.Next[n] == nil {
			this.Next[n] = new(Trie)
		}
		this = this.Next[n]
	}
	this.IsEnd = true
}

/** Returns if the word is in the trie. */
func (this *Trie) Search(word string) bool {
	that := this.searchPrefix(word)
	return that != nil && that.IsEnd == true
}

/** Returns if there is any word in the trie that starts with the given prefix. */
func (this *Trie) StartsWith(prefix string) bool {
	that := this.searchPrefix(prefix)
	return that != nil
}

func (this *Trie) searchPrefix( word string) *Trie {
	for i := 0 ; i < len(word) ; i ++ {
		n := word[i] - 'a'
		if this.Next[n] == nil {
			return nil
		}
		this = this.Next[n]
	}
	return this
}
```
```java
class Trie {
    private boolean isEnd ;
    private Trie[]  next  ;

    public Trie() {
        isEnd = false ;
        next  = new Trie[26] ;
    }

    // 将字符串插入到字典树
    public void insert( String word ) {
        if ( word == null || word .length() == 0 ) return;
        Trie curr = this ;
        char[] words = word.toCharArray() ;
        for (char c : words) {
            int n = c - 'a';
            if (curr.next[n] == null) curr.next[n] = new Trie();
            curr = curr.next[n];
        }
        curr.isEnd = true ;
    }

    // 寻找字符串是否在字典树上
    public boolean search( String word ) {
        Trie node = searchPrefix(word) ;
        return node != null && node.isEnd ;
    }

    public boolean startsWith( String prefix ) {
        Trie node = searchPrefix(prefix);
        return node != null ;
    }


    private Trie searchPrefix( String word ) {
        Trie node = this ;
        char[] words = word.toCharArray();
        for (char c : words) {
            node = node.next[c - 'a'];
            if (node == null) return null;
        }
        return node ;
    }
}
```