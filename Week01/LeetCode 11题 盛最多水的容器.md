## Java 暴力
```java
int maxHeight = 0;
for( int i = 0 ; i < height.length - 1; i++ ) {
	for (int j = i - 1 ; j < height.length ; j++) {
		int minHeight = height[i] > height[j] ? height[j] : height[i] ;
		int area = ((j - i) * minHeight);
		maxHeight = area > maxHeight ? area : maxHeight;
	}
}
System.out.println(maxHeight);
```

## Go
```go
func maxArea(height []int) int {
    i,j := 0,len(height) - 1
	max,hg := 0,0
	for i < j {
		if height[i] > height[j] {
			hg = (j - i) * height[j]
			j --
		} else {
			hg = (j - i) * height[i]
			i ++
		}
		if max < hg {
			max = hg
		}
	}
    return max
}
```

## Java 
```java
int left = 0;  // 左指针
int right = height.length - 1 ; // 右指针 (这里的减1，指的是数组真正的下标)
int maxHeight = 0; // 记录最大的面积
int area = 0;  // 临时记录
// 如果在循环中 左边 <= 右边 代表循环中止
while (left <= right) {
	// 那个边小那个边下标移动
	// 乘 小的一边
	if(height[left] > height[right]) {
		area = (( right - left ) * height[right]); 
	} else {
		area = (( right - left ) * height[left]); 
	}
	maxHeight = maxHeight > area ? maxHeight : area ;
} 
System.out.println(maxHeight);
```

## Python 
```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        i = 0
        j = len(height) - 1
        maxheight = 0
        while i <= j :
            if height[i] > height[j] :
                maxheight = max((j - i) * height[j],maxheight)
                j = j - 1
            else :
                maxheight = max((j - i) * height[i], maxheight)
                i = i + 1
        return  maxheight
```        

## C 
```c
int maxArea(int* height, int heightSize){
    int i = 0 ;
    int j = heightSize - 1;
    int hg = 0;
    int max = 0;
    while(i < j) {

        if( height[i] > height[j] ) {
            hg = ( j - i ) * height[j];
            j -- ;
        } else {
            hg = ( j - i ) * height[i];
            i ++;
        }
        max = max > hg ? max : hg ;
    }

    return max;
}
```

## PHP
```php
class Solution {

    /**
     * @param Integer[] $height
     * @return Integer
     */
    function maxArea($height) {
        
        $i = 0;
        $j = count($height) - 1 ;
        $max = 0;
        while( $i < $j ) {
            
            if($height[$i] >  $height[$j] ) {
                $hg = ($j - $i) * $height[$j];
                $j -- ;
            } else {
                $hg = ( $j - $i ) * $height[$i];
                $i ++ ;
            }

            $max = $max > $hg ? $max : $hg ;
        }

        return $max;
    }
}
```