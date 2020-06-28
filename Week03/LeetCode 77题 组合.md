
#### Java 
##### 自己写的 Java
```java
class Solution {
    public List<List<Integer>> combine(int n, int k) {
        List<List<Integer>> res  = new LinkedList<>();
        LinkedList<Integer> list = new LinkedList<>();
        return backcombine(list,res,n,k,1);
    }

    public List<List<Integer>> backcombine(LinkedList<Integer> list ,
                                            List<List<Integer>> res ,
                                            int n,int k,int start ) {

        if(list.size() == k) {
            res.add(new ArrayList<>(list));
            return res;
        }

        for ( int i = start ; i <= n ; i ++) {
            list.add(i);
            res = backcombine(list,res,n,k, i + 1);
            list.remove(list.size() - 1);
        }

        return res;
    }
}
```

#### 国际站 大神的作品 自己欣赏 ～  nice
```java
class Solution {
    public List<List<Integer>> combine(int n, int k) {
        List<List<Integer>> result = new ArrayList<>();

        if ( k > n || k < 0 ) {
            return result ;
        }

        if ( k == 0 ) {
            result.add(new ArrayList<Integer>());
            return result ;
        }

        result = combine( n - 1 , k - 1) ;
        for ( List<Integer> list : result) {
            list.add(n);
        }

        result.addAll(combine(n - 1 , k ));
        return result ;
    }

}
```

#### 自己写的 GO
```GO
func combine(n int, k int) [][]int {
    return backcombine([]int{},[][]int{},n,k,1)
}

func backcombine(list []int ,res [][]int , n int , k int , start int) [][]int {
	if len(list) == k {
		temp := make([]int , len(list))
		copy(temp,list)
		res = append(res , temp)
		return res
	}

	for i := start ; i <= n ; i ++ {
		list = append(list , i)
		res = backcombine(list , res , n , k ,i + 1)
		list = list[:len(list) - 1]
	}
	return res
}
```

#### 根据国际站 大佬的思路 模拟出的GO代码
##### 这个代码我感觉非常的好。真的是长见识 ~~~ 非常的简洁明了
```GO
func combine(n int, k int) [][]int {
    res := [][]int{}

	if k > n || k < 0 {
		return res
	}

	if k == 0 {
		res = append(res, []int{})
		return res
	}

	res = combine(n - 1 , k - 1)
	for i := 0 ; i < len(res) ; i ++ {
		res[i] = append(res[i], n)
	}

	temp := combine(n - 1 , k)
	for i := 0 ; i < len(temp) ; i ++ {
		res = append(res, temp[i])
	}

	return res
}
```