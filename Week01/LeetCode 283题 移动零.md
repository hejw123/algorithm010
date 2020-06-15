## Java
```java
class Solution {
    public void moveZeroes(int[] nums) {
        int j = 0;
        for (int i = 0 ; i < nums.length ; i++) {
            if(nums[i] != 0) {
                nums[j] = nums[i];
                if( i != j ) {
                     nums[i] = 0 ;
                }
                j ++ ;
            }
        }
    }
}
```

## C 
```c
void moveZeroes(int* nums, int numsSize){
    int i = 0;
    int j = 0;

    for (i = 0; i < numsSize ; i ++) {

        if( nums[i] != 0 ) {

            nums[j] = nums[i] ;
            if(i != j) {
                nums[i] = 0;
            }
            j ++;
        }
    }
}
```

## Go
```go
func moveZeroes(nums []int)  {

    j := 0
	for i := 0; i < len(nums); i ++ {
		if nums[i] != 0 {
			nums[j] = nums[i]
			if i != j {
				nums[i] = 0
			}
			j ++ 
		}
	}

    fmt.Println(nums)
}
```

## Python 
```python
j = 0
for i in range(len(nums)):
    if nums[i] != 0 :
        nums[j] = nums[i]
        if i != j :
            nums[i] = 0
        j = j + 1

return nums
```
## PHP 
```php
function moveZeroes(&$nums) {
    $j = 0;
    for ($i = 0 ; $i < count($nums) ; $i ++) {
        if($nums[$i] !== 0) {
            $nums[$j] = $nums[$i];
            if($i !== $j) {
                $nums[$i] = 0 ;
            }
            $j ++ ;
        }
    }
    return $nums;
}
```