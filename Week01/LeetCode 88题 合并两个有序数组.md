## Java 
```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int i = m - 1;
        int j = n - 1 ;
        int p = m + n - 1 ;

        while ( p > -1 ) {
            if( j > -1 && i > -1) {
                nums1[p--] = nums1[i] > nums2[j] ? nums1[i--] : nums2[j--] ;
            } else if (j == -1) {
                nums1[p--] = nums1[i--];
            } else if (i == -1) {
                nums1[p--] = nums2[j--];
            }
        }
    }
}
```

## Go 
```go
func merge(nums1 []int, m int, nums2 []int, n int)  {
    start , end , p := m - 1 ,n - 1 , m + n - 1
	for p > -1 {
		if start > -1 && end > -1 {
			if(nums1[start] > nums2[end]) {
				nums1[p] = nums1[start]
				start --
			} else {
				nums1[p] = nums2[end]
				end --
			}
		}else if start == -1 {
			nums1[p] = nums2[end]
			end --
		} else if end == -1 {
			nums1[p] = nums1[start]
			start --
		}
		p --
	}
}
```