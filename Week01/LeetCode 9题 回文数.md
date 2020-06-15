## Go 自己思考出来的 就很长～～～
```go
func isPalindrome(x int) bool {
	// 因为所有的负数都不是回文数 不包括0的所有能被10整除的都不是回文数
    if x < 0 || (x % 10 == 0 && x != 0) {
        return false
    }
    // 所有的小于10的正整数 都是回文数
    if x >= 0 && x <= 9 {
        return true
    }
    number := []int{}
	for x != 0 {
		i := x % 10
		number = append(number,i)
		x = x / 10
	}

	left := 0;
	right := len((number)) -1 ;
	// 移动两边的指针 
	for left < right {
		if number[right] != number[left] {
			// 只要发现两边指针 指向的数 不相同直接返回 
			return false
		}
		left ++ ;
		right --;
	}
	
	// 最后返回 
	return true
}
```

## Java 寻找一半的对对应的一半是不是相等
```java
class Solution {
    public boolean isPalindrome(int x) {
        // 前面的特殊条件判读的一样
        if( x < 0 || (x % 10 == 0 && x != 0)) return false;
		if( x >= 0 && x <= 9 ) return true ;
		
        int nb = 0;
        while (x > nb) {
            nb = nb * 10 + x % 10;
            x = x / 10;
        }
        // 因为奇数个 和 偶数个区别  121  最后 nb = 12  x = 1 
        // 所以 要双重判断 
        return ( nb == x || nb / 10 == x) ;
    }
}
```

## Python 极其简单 
```python
class Solution:
    def isPalindrome(self, x: int) -> bool:
    	// 就这一行代码 搞定！
        return str(x)[::-1] == str(x)
```