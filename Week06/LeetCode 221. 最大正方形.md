## Java 
```java
class Solution {
    public int maximalSquare(char[][] matrix) {
        if ( matrix == null || matrix.length == 0 || matrix[0].length == 0 ) {
            return 0 ; 
        }
        int[][] dp = new int[matrix.length][matrix[0].length];
        int maxSquare = 0 ;
        for ( int i = 0 ; i < matrix.length ; i ++ ) {
            for ( int j = 0 ; j < matrix[0].length ; j ++) {
                if (matrix[i][j] == '1') {
                    if (i == 0 || j == 0 ) {
                        dp[i][j] = 1 ;
                    } else {
                        dp[i][j] = Math.min(dp[i - 1][j] , Math.min(dp[i][j - 1], dp[i - 1][j - 1])) + 1;
                    }
                    maxSquare = Math.max(dp[i][j], maxSquare) ;
                }
            }
        }
        return maxSquare * maxSquare ;
    }
}
```
```go
func maximalSquare(matrix [][]byte) int {
    dp := make([][]int , len(matrix))
	for i := 0 ; i < len(matrix) ; i ++ {
		dp[i] = make([]int,len(matrix[i]))
	}
	maxSquare := 0
	min := func(a ,b int) int {
		if a < b {
			return a
		}
		return b
	}
	max := func( a , b int) int {
		if a > b {
			return a
		}
		return b
	}
	for i := 0 ; i < len(matrix) ; i ++ {
		for j := 0 ; j < len(matrix[0]) ; j ++ {
			if matrix[i][j] == '1' {
				if j == 0 || i == 0 {
					dp[i][j] = 1
				} else {
					dp[i][j] = min (min(dp[i - 1][j] , dp[i][j - 1] ), dp[i - 1][j - 1]) + 1
				}
				maxSquare  = max(maxSquare , dp[i][j])
			}
		}
	}
	return maxSquare * maxSquare
}
```