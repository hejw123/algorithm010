## Java 暴力解决 
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        if (nums == null || nums.length < 3) return  Collections.emptyList();
        Set<List<Integer>> result = new LinkedHashSet<>();
        Arrays.sort(nums);
        for (int i = 0 ; i < nums.length - 2 ; i ++) {
            for (int j = i + 1 ; j < nums.length - 1 ; j++) {
                for (int k = j + 1 ; k < nums.length ; k ++) {
                    if(nums[i] + nums[j] + nums[k] == 0) {
                        List<Integer> value = Arrays.asList(nums[i],nums[j],nums[k]);
                        result.add(value) ;
                    }
                }
            }
        }
        return new ArrayList<>(result);
    }
}

## Go 暴力解决 
func threeSum(nums []int) [][]int {
    var result [][]int
	sort.Ints(nums)
	if nums == nil || len(nums) < 3  {
		return result
	}

	HashMap := map[string]string{}

	for i := 0 ; i < len(nums) - 2 ; i ++  {
		for j := i + 1; j< len(nums) - 1 ; j ++ {
			for k := j + 1 ; k < len(nums) ; k ++  {
				if nums[i] + nums[j] + nums[k] == 0 {
					tmp := []int{nums[i],nums[j],nums[k]}

					if _ , ok := HashMap[fmt.Sprint(tmp)] ; !ok {
						result = append(result,tmp)
					}

					HashMap[fmt.Sprint(tmp)] = "1"
				}
			}
		}
	}

	return result
}

## Java 两次暴力 一层hash表
public static List<List<Integer>> HashdirectlySolution(int[] nums) {
    //  a + b = -c  a = -c - b
    if( nums == null || nums.length < 3 ) return Collections.emptyList();

    Set<List<Integer>> result = new LinkedHashSet<>();

    for (int i = 0 ; i< nums.length - 2 ; i ++ ) {
        // -c
        int target = -nums[i];

        Map<Integer , Integer> hashMap = new HashMap<>(nums.length - i);

        for (int j = i + 1 ; j < nums.length ; j ++) {

            int v = target - nums[j];

            Integer exist = hashMap.get(v) ;

            if(exist != null) {
                List<Integer> list = Arrays.asList(nums[i],exist,nums[j]);
                list.sort(Comparator.naturalOrder());
                result.add(list);
            } else {
                hashMap.put(nums[j],nums[j]);
            }
        }
    }

    return new ArrayList<>(result);
}

## Go 
func HashdirectlySolution(nums[] int) [][] int{

	var result [][]int;
	if nums == nil || len(nums) < 3  {
		return result
	}
	sort.Ints(nums)
	HashAll := map[string]int{}
	for i:=0 ; i<len(nums) - 2 ; i++  {
		targer := -nums[i]
		HashMap := map[int]int{}
		for j:= i+1; j < len(nums) ; j++ {
			tmp := targer - nums[j]

			if v , ok := HashMap[tmp] ; ok {

				arr := []int{nums[i],v,nums[j]}
				if  _ , ok2 := HashAll[fmt.Sprint(arr)] ; !ok2 {
					result = append(result, arr)
				}
				HashAll[fmt.Sprint(arr)] = v
			}

			HashMap[nums[j]] = nums[j]
		}
	}
	return result
}

## Java 双指针移动 
public static List<List<Integer>> doubledirectlySolution(int[] nums) {
    //  a + b = -c  a = -c - b
    if( nums == null || nums.length < 3 ) return Collections.emptyList();
    Arrays.sort(nums);
    Set<List<Integer>> result = new LinkedHashSet<>();
    for (int i = 0 ; i< nums.length - 2 ; i ++ ) {
        if( nums[i] > 0 ) break;
        if( i > 0 && nums[i] == nums[i - 1] ) continue;
        int k = i + 1 , j = nums.length - 1;
        while ( k < j) {
            int sum = nums[i] + nums[j] + nums[k] ;
            if( sum > 0 ) {
                while ( k < j && nums[j] == nums[--j]) ;
            } else if(sum < 0) {
                while ( k < j && nums[k] == nums[++k]) ;
            } else {
                List<Integer> list = Arrays.asList(nums[i],nums[j],nums[k]);
                result.add(list);
                while ( k < j && nums[j] == nums[--j]) ;
                while ( k < j && nums[k] == nums[++k]) ;
            }
        }
    }
    return new ArrayList<>(result);
}


## Go 双指针移动
func doubledirectlySolution(nums[] int) [][] int{
	var result [][]int
	if nums == nil || len(nums) < 3 {
		return result
	}

	sort.Ints(nums)
	for i := 0 ; i < len(nums) - 2 ; i ++  {
		if nums[i] > 0 { break }
		if i > 0 && nums[i] == nums[i - 1] { continue }
		k , j := i + 1 , len(nums) - 1

		for k < j {
			sum := nums[i] + nums[k] + nums[j]
			if ( sum > 0 ) {
				for k < j && nums[j] == nums[j - 1]  { j -- }
				j = j - 1
			} else if ( sum < 0 ){
				for k < j && nums[k] == nums[k + 1]  { k ++ }
				k = k + 1
			} else {
				result = append(result, []int{nums[i] , nums[k] , nums[j]})
				for k < j && nums[j] == nums[j - 1]  { j -- }
				for k < j && nums[k] == nums[k + 1]  { k ++ }
				j = j - 1
				k = k + 1
			}
		}
	}
	return result
}
