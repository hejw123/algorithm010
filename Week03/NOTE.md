## 第三周总结 
### 递归代码模版
#### Python 代码模板
```python
def recursion(level, param1, param2, ...): 
    # 结束条件
    if level > MAX_LEVEL: 
	   process_result 
	   return 

    # 逻辑处理  
    process(level, data...) 
    
    # 递归开始
    self.recursion(level + 1, p1, ...) 
   
    # 初始化数据
```
#### Java 代码模板
```java
public void recur(int level, int param) { 
  // terminator 
  if (level > MAX_LEVEL) { 
    // process result 
    return; 
  }
  // process current logic 
  process(level, param); 
  // drill down 
  recur( level: level + 1, newParam); 
  // restore current status 
}
```

### 分治代码模板
#### Python 代码模板
```python
def divide_conquer(problem, param1, param2, ...): 
  # recursion terminator 
  if problem is None: 
	print_result 
	return 
  # prepare data 
  data = prepare_data(problem) 
  subproblems = split_problem(problem, data) 
  # conquer subproblems 
  subresult1 = self.divide_conquer(subproblems[0], p1, ...) 
  subresult2 = self.divide_conquer(subproblems[1], p1, ...) 
  subresult3 = self.divide_conquer(subproblems[2], p1, ...) 
  …
  # process and generate the final result 
  result = process_result(subresult1, subresult2, subresult3, …)
	
  # revert the current level states
```

##### BFS
1. 初始化一个队列
2. 队列中先把第一个节点放进去，作为启动节点，不然后面没法while启动起来
3. 队列中出一个节点，处理，然后把它的所有子节点拿出来，依次放入队列中
总结
1. 初始节点在循环外放进去
2. 处理节点逻辑和生成子节点逻辑放到循环内

#### 个人理解
##### 回溯
回溯就是去盗梦空间的下层梦境尝试一下，如果发现不行，就回到现实重头再来~
回溯和分治之类的，其实都是运用的递归的能力，来实现的一种思想
1. 终止条件
2. 当前层处理
3. drill down下钻
4. 清理现场
