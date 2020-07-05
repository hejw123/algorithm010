#### GO
```go
func jump(nums []int) int {
    jump ,  end , max  := 0 ,0 ,0
	for i := 0 ; i < len(nums) - 1 ; i ++ {
		if i + nums[i] > max {
			max = i + nums[i] 
		}
		if i == end {
			end = max 
			jump ++ 
		} 
	}
	return jump 
}
```
#### java
```java
class Solution {
    public int jump(int[] nums) {
        int jump = 0 ;
        int end  = 0 ;
        int max  = 0 ;
        for ( int i = 0 ; i < nums.length - 1 ; i ++) {
            max = Math.max(i + nums[i] , max);
            if ( i == end ) {
                end = max ;
                jump ++ ;
            }
        }
        return jump ;
    }
}
```