#### GO 
```go
// DFS
func numIslands(grid [][]byte) int {
    if grid == nil || len(grid) == 0 || len(grid[0]) == 0 {
		return 0 ;
	}

	x , y , sum := len(grid) , len(grid[0]) , 0

	for i := 0 ; i < x ; i ++ {
		for j := 0 ; j < y ; j ++ {
			if grid[i][j] == '1' {
				sum = sum + 1
				DFS(&grid,i,j)
			}
		}
	}
	return sum ;
}
func DFS(grid *[][]byte, x int , y int  ) {

	if x < 0 || y < 0 || x >= len(*grid) || y >= len((*grid)[0]) || (*grid)[x][y] == '0'{
		return ;
	}

	(*grid)[x][y] = '0';

	DFS(grid , x , y - 1)
	DFS(grid , x , y + 1)
	DFS(grid , x - 1, y )
	DFS(grid , x + 1, y )
}
```
#### java
```java
class Solution {
    public int numIslands(char[][] grid) {

        if ( grid == null || grid.length == 0 ) {
            return 0;
        }

        int row = grid.length ;
        int cow = grid[0].length ;
        int sum = 0 ;

        for ( int i = 0 ; i < row ; i ++ ) {
            for ( int j = 0; j < cow ; j ++ ) {
                if (grid[i][j] == '1') {
                    sum = sum + 1;
                    DFS(grid,i,j);
                }
            }
        }

        return sum;
    }

    public void DFS(char[][]grid , int x , int y) {

        if (x < 0 || y < 0 || x >= grid.length || y >= grid[0].length || grid[x][y] == '0') {
            return ;
        }

        grid[x][y] = '0';

        DFS(grid, x , y - 1);
        DFS(grid, x , y + 1 );
        DFS(grid, x -1 , y);
        DFS(grid, x + 1 ,y);
    }
}
```