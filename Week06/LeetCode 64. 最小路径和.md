## java 
```java
class Solution {
    public int minPathSum(int[][] grid) {
        int[][] dp = grid ;

        for ( int i = 0 ; i < grid.length ; i ++) {
            for ( int j = 0 ; j < grid[0].length ; j ++ ) {
                if ( i == 0 && j == 0 ){
                    continue;
                } else if ( i == 0 && j != 0 ) {
                    dp[i][j] = dp[i][j - 1] + dp[i][j] ;
                } else if ( i != 0 && j == 0) {
                    dp[i][j] = dp[i][j] + dp[i - 1][j] ;
                } else {
                    dp[i][j] = Math.min(dp[i - 1][j],dp[i][j - 1]) + dp[i][j] ;
                }
            }
        }
        
        return dp[grid.length - 1][grid[0].length - 1] ;
    }
}
```
## GO
```go
func minPathSum(grid [][]int) int {
    Min := func( a int, b int) int {
		if a < b {
			return a
		}
		return b
	}
	dp := grid
	for i := 0 ; i < len(grid) ; i ++ {
		for j := 0 ; j < len(grid[0]) ; j ++ {
			if i == 0 && j == 0 {
				dp[i][j] = grid[i][j]
			} else if  i == 0 && j != 0  {
				dp[i][j] = grid[i][j] + grid[i][j - 1]
			} else if  i != 0 && j == 0 {
				dp[i][j] = grid[i][j] + grid[i - 1][j]
			} else {
				dp[i][j] = Min(grid[i - 1][j],grid[i][j - 1]) + grid[i][j]
			}
		}
	}
	return dp[len(grid) - 1][len(grid[0]) - 1]
}
```