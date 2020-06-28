#### Java 
```java
class Solution {
    public List<List<Integer>> permute(int[] nums) {
        List<Integer> tempList = new LinkedList<>();
        List<List<Integer>> list = new LinkedList<>();
        for ( int v : nums) {
            tempList.add(v) ;
        }
        helper(tempList,list,0,nums.length);
        return list;
    }

    public void helper (List<Integer> tempList ,
                                       List<List<Integer>> list ,
                                       int start , int end) {

        // 结束条件
        if (start == end) {
            list.add(new LinkedList<Integer>(tempList));
            return ;
        } else {
            for ( int i = start ; i < end ; i ++) {
                Collections.swap(tempList, i, start);
                helper(tempList,list,start + 1 , end);
                Collections.swap(tempList, start, i);
            }
        }
    }
}
```

#### GO
```Go
func permute(nums []int) [][]int {
    list := [][]int{}
    return backtrack(nums,list,0,len(nums))
}

func backtrack (nums []int , list [][]int , start int , end int) [][]int {

    if start == end {
        temp := make([]int,len(nums))
        copy(temp , nums)
        list = append(list , temp)
        return list 
    }

    for i := start ; i < end ; i ++ {

        nums[i] , nums[start] = nums[start] , nums[i]

        list = backtrack( nums, list, start + 1 , end ) 

        nums[i] , nums[start] = nums[start] , nums[i]
    }

    return list 
}
```