#### Java 
```java
class Solution {
    public List<List<Integer>> permuteUnique(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        if (nums==null || nums.length==0) { return ans; }
        permute(ans, nums, 0);
        return ans;
    }
    
    private void permute(List<List<Integer>> ans, int[] nums, int index) {
        if (index == nums.length) { 
            List<Integer> temp = new ArrayList<>();
            for (int num: nums) { temp.add(num); }
            ans.add(temp);
            return;
        }
        Set<Integer> appeared = new HashSet<>();
        for (int i=index; i<nums.length; ++i) {
            if (appeared.add(nums[i])) {
                swap(nums, index, i);
                permute(ans, nums, index+1);
                swap(nums, index, i);
            }
        }
    }
    
    private void swap(int[] nums, int i, int j) {
        int save = nums[i];
        nums[i] = nums[j];
        nums[j] = save;
    }
}
```

#### GO
```Go
func permuteUnique(nums []int) [][]int {
    sort.Ints(nums)
	used := make([]bool,len(nums))
	res := [][]int{}
	list := []int{}
	return backtrack(nums,res,list,used)
}
func backtrack (nums []int , res [][]int ,list []int, user []bool) [][]int {

	if len(list) == len(nums) {
		temp := make([]int,len(list))
		copy(temp , nums)
		res = append(res , list)
		return res
	}

	for i := 0 ; i < len(nums) ; i ++ {

		if  user[i] || (i > 0  && nums[i - 1] == nums[i] && !user[i - 1]) {
			continue
		}
		user[i] = true
		list = append(list, nums[i])
		res = backtrack( nums, res ,list ,user )
		user[i] = false
		tmp := make([]int,len(list) - 1)
		copy(tmp,list[:len(list) - 1])
		list = tmp
	}

	return res
}
```