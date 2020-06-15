## Java
```java
/**
 * 因为在加一的过程中 如果是 9 或者 99 这种 加一之后 除了首位以外都是0
 * 在数组循环过程中，如果对数字加一后取个位是不是等于0如果等于0 说明运算结果为10那么就应该前一位加一 ，如此循环。  
 */ 
class Solution {
    public int[] plusOne(int[] digits) {
        for ( int i = digits.length - 1 ; i >= 0 ; i--) {

            digits[i] = digits[i] + 1 ;
            digits[i] = digits[i] % 10;

            if(digits[i] != 0) {
                return digits;
            }
        }

        int[] plus = new int[digits.length + 1];
        plus[0] = 1;
        return plus;
    }
}
```

## Go
```go
func plusOne(digits []int) []int {

	for v := len(digits) - 1 ; v >= 0 ; v -- {
		digits[v] ++ ;
		digits[v] = digits[v] % 10
		if( digits[v] != 0 ) {
			return digits
		}
	}

	plus := make([]int,len(digits) + 1)
	plus[0] = 1
	return plus
}
```
