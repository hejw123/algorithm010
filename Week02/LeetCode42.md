# Java
## 排序 
```java
public boolean isAnagram(String s, String t) {
    if (s.length() != t.length()) {
        return false;
    }
    char[] str1 = s.toCharArray();
    char[] str2 = t.toCharArray();
    Arrays.sort(str1);
    Arrays.sort(str2);
    return Arrays.equals(str1, str2);
}
```
## Hash表 ： 方法1 判断表中存在的值是不是等于 0 
```java
class Solution {
    public boolean isAnagram(String s, String t) {
        
        if (s.length() != t.length()) return false;

        int[] counter = new int[26];

        for (int i = 0 ; i < s.length() ; i++) {
            counter[s.charAt(i) - 'a'] ++ ;
            counter[t.charAt(i) - 'a'] -- ;
        }

        for ( int v : counter ) {
            if (v != 0) return false ;
        }
        return true;
    }
}
```
## Hash表 ： 方法2 先计算一下字符出现的次数，后判断是不是包含 或者 不等
```java
public boolean isAnagram(String s, String t) {
    if (s.length() != t.length()) {
        return false;
    }
    int[] table = new int[26];
    for (int i = 0; i < s.length(); i++) {
        table[s.charAt(i) - 'a']++;
    }
    for (int i = 0; i < t.length(); i++) {
        table[t.charAt(i) - 'a']--;
        if (table[t.charAt(i) - 'a'] < 0) {
            return false;
        }
    }
    return true;
}
```

# Go
```go
// 因为在go中无法直接使用 字符串排序 。 这里直接使用Hash表法 
func isAnagram(s string, t string) bool {
    if len(s) != len(t) { return false }
	lenght := [26]int{}
    
	for k := 0 ; k < len(s) ; k ++ {
		lenght[int(s[k])-97] ++ ;
		lenght[int(t[k])-97] -- ;
	}

	for _ , k := range lenght {
		if k != 0 { return false }
	}
	return true
}
``` 