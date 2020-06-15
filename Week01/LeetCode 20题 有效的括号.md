## Java 栈的数据结构就可以解决
```java
public static boolean isValid(String s) {
	// 两种特殊情况 一种空 另外是 奇数 
    if(s.length() == 0 ) return true ;
    if(s.length() % 2 != 0) return false ;
    // 创建栈
    Stack<Character> stack = new Stack<Character>();
    for ( char c : s.toCharArray()) {
        if (c == '(' ) {
            stack.push(')');
        } else if ( c == '{') {
            stack.push('}');
        } else if ( c == '[') {
            stack.push(']');
        } else if ( stack.isEmpty() || stack.pop() != c ){
           return false ;
        }
    }
    return stack.isEmpty();
}
```

## Go 数组解决
```go
func isValid(s string) bool {
	if len(s) == 0 { return true }
	if len(s) % 2 != 0 { return false }
	subscript := 0
	sub := make([]int,len(s))
	for i := 0 ; i < len(s) ; i++ {
		if s[i] == 40 {
			sub[subscript] = 41
			subscript ++
		} else if s[i] == 91 {
			sub[subscript] = 93
			subscript ++
		} else if s[i] == 123 {
			sub[subscript] = 125
			subscript ++
		} else {
			subscript --
			if subscript == -1 || int(s[i]) != sub[subscript] {
				return false
			}
			sub[subscript] = 0
		}
	}

	return subscript == 0 || (subscript != len(s) && sub[subscript - 1] == 0)
}
```