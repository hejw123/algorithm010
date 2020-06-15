## Java 暴力解法
```java
int[] subscript = new int[2];
// 这里的 length - 1 只需要循环到数组前一个数即可
for (int i = 0 ; i < nums.length - 1 ; i ++) { 
	// 这里的 i + 1 是指的的 第二个数要是在第一个数的后面
	for (int j = i + 1 ; j < nums.length ; j ++) {
		if (nums[i] + nums[j] == target) {
			subscript[0] = i ;
			subscript[1] = j ;
			return subscript ;
		}
	}
}
return subscript ;
```

## Java 哈希表
```java
Map<Integer , Integer >HashSum = new HashMap<>();
for (int i = 0 ; i < nums.length ; i ++) {
    int complement = target - nums[i] ;
    if(HashSum.containsKey(nums[i])) {
        return new int[]{HashSum.get(nums[i]),i};
    }
    HashSum.put(complement,i);
}
return new int[2] ;
```

## Go 
```go
// go 的 map 实现是用 hash表完成的
Map := map[int]int{}
for i , v:= range nums {
	if k , ok := Map[v] ; ok  {
		return []int{k,i}
	}
	Map[target - v] = i
}
return []int{}
```

## Python 其实是用 Python字典
```python
hashMap = {}
for i,num in enumerate(nums) :
    if hashMap.get(num) is not None :
        return [hashMap.get(num),i]
    hashMap[target - num] = i
return []
```

## PHP 数组特殊性
```php
function twoSum($nums, $target) {
    $twonums = array(); // 创建数组
    // 循环 并判断是不是存在 数组中 
    foreach ( $nums as $k => $v ) {
        if(isset($twonums[$v])) {
         	// 如果存在直接返回
            return array($twonums[$v],$k);
        }
        $twonums[ $target - $v ] =  $k ;
    } 
    // 返回数组
    return array();
 }
```

