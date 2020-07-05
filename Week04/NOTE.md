# 第四周 深度优先搜索、广度优先搜索
## 搜索 - 遍历 
1. 每一个节点都要访问一次
2. 每一个节点仅仅要访问一次
3. 对于节点的访问顺序不限
    -   深度优先搜索 ： depth   first search (DFS)
    -   广度优先搜索 ： breadth frist search (BFS)
    -   优先级优先填报 : 
        - 应用在各种推荐算法

### 深度优先搜索
#### 递归
```python
visited = set() 
def dfs(node, visited):
    if node in visited: # terminator
    	# already visited 
    	return 
	visited.add(node) 
	# process current node here. 
	...
	for next_node in node.children(): 
		if next_node not in visited: 
			dfs(next_node, visited)
```
#### 非递归
```python
def DFS(self, tree): 
	if tree.root is None: 
		return [] 
	visited, stack = [], [tree.root]
	while stack: 
		node = stack.pop() 
		visited.add(node)
		process (node) 
		nodes = generate_related_nodes(node) 
		stack.push(nodes) 
	# other processing work 
	...
```
### 广度优先搜索
```python
def BFS(graph, start, end):
    visited = set()
	queue = [] 
	queue.append([start]) 
	while queue: 
		node = queue.pop() 
		visited.add(node)
		process(node) 
		nodes = generate_related_nodes(node) 
		queue.push(nodes)
	# other processing work 
	...
```

### 贪心算法
#### 解释
用局部最优来整体规划 
#### 注意事项
必须能够确定 局部最优等于整体最优

### 二分查找
### 前提 
1. 目标函数单调性（单调递增 或 单调递减）
2. 存在边界上下边界(左右)
3. 能够通过索引访问
 
### 代码模版
```Python
left, right = 0, len(array) - 1 
while left <= right: 
	  mid = (left + right) / 2 
	  if array[mid] == target: 
		    # find the target!! 
		    break or return result 
	  elif array[mid] < target: 
		    left = mid + 1 
	  else: 
		    right = mid - 1

```
```java
int left = 0 , right = array.length - 1
while (left <= right) {
	int mid = left + ( right -left ) / 2

	if ( array[mid] == target ) {
		// return 
		break ; 
	} else if ( array[mid] > target ) {
		right = mid - 1
	} else {
		left = mid + 1
	}
}
```
