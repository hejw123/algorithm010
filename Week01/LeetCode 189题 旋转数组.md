## Java (使用额外的空间)
public static void rotate2(int[] nums, int k){
    int[] nums2 = new int[nums.length];
    for (int i = 0 ; i < nums.length ; i ++) {
        nums2[(i + k) % nums.length] = nums[i];
    }
    for (int j = 0 ; j < nums2.length ; j++) {
       nums[j] = nums2[j];
    }
}

## Go (使用额外的空间)
func rotate(nums []int, k int)  {
	nums2 := make([]int,len(nums))
	for i , v := range nums {
		nums2[( i + k) % len(nums)] = v
	}
	for i ,v := range nums2 {
		nums[i] = v
	}
}

## Java 反转数组
class Solution {
    public void rotate(int[] nums, int k) {
        k %= nums.length;
        reverse(nums, 0, nums.length - 1);
        reverse(nums, 0, k - 1);
        reverse(nums, k, nums.length - 1);
    }

    public void reverse(int[] nums, int start, int end) {
        while (start < end) {
            nums[start] = nums[start] ^ nums[end] ;
            nums[end]   = nums[start] ^ nums[end] ;
            nums[start] = nums[start] ^ nums[end] ;
            start++;
            end--;
        }
    }
}

## Go 
func reverse (nums[] int , start int , end int) {
	for start < end {
		nums[start] ,nums[end] = nums[end] ,nums[start]
		start ++
		end --
	}
}
func reverserotate(nums []int, k int)  {
	k = k % len(nums)
	reverse(nums , 0 , len(nums) - 1 )
	reverse(nums , 0 , k - 1 )
	reverse(nums ,  k ,len(nums) - 1)
}
