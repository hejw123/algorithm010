```go
type LRUCache struct {
    size int
    capacity int
    cache map[int]*DLinkedNode
    head, tail *DLinkedNode
}

type DLinkedNode struct {
    key, value int
    prev, next *DLinkedNode
}

func initDLinkedNode(key, value int) *DLinkedNode {
    return &DLinkedNode{
        key: key,
        value: value,
    }
}

func Constructor(capacity int) LRUCache {
    l := LRUCache{
        cache: map[int]*DLinkedNode{},
        head: initDLinkedNode(0, 0),
        tail: initDLinkedNode(0, 0),
        capacity: capacity,
    }
    l.head.next = l.tail
    l.tail.prev = l.head
    return l
}

func (this *LRUCache) Get(key int) int {
    if _, ok := this.cache[key]; !ok {
        return -1
    }
    node := this.cache[key]
    this.moveToHead(node)
    return node.value
}


func (this *LRUCache) Put(key int, value int)  {
    if _, ok := this.cache[key]; !ok {
        node := initDLinkedNode(key, value)
        this.cache[key] = node
        this.addToHead(node)
        this.size++
        if this.size > this.capacity {
            removed := this.removeTail()
            delete(this.cache, removed.key)
            this.size--
        }
    } else {
        node := this.cache[key]
        node.value = value
        this.moveToHead(node)
    }
}

func (this *LRUCache) addToHead(node *DLinkedNode) {
    node.prev = this.head
    node.next = this.head.next
    this.head.next.prev = node
    this.head.next = node
}

func (this *LRUCache) removeNode(node *DLinkedNode) {
    node.prev.next = node.next
    node.next.prev = node.prev
}

func (this *LRUCache) moveToHead(node *DLinkedNode) {
    this.removeNode(node)
    this.addToHead(node)
}

func (this *LRUCache) removeTail() *DLinkedNode {
    node := this.tail.prev
    this.removeNode(node)
    return node
}
```

```java
class LRUCache {

    class DLinkedNode{
        int key ;
        int value ;
        DLinkedNode prev ;
        DLinkedNode next ;
        public DLinkedNode() {}
        public DLinkedNode( int _key , int _value ) { key = _key ; value = _value ; }
    }

    private Map<Integer , DLinkedNode > cache = new HashMap<>();
    private int size ;
    private int capacity ;
    private DLinkedNode head , tail ;

    public LRUCache(int capacity){
        this.size = 0 ;
        this.capacity = capacity ;
        // 使用伪头部和伪尾部节点
        head = new DLinkedNode() ;
        tail = new DLinkedNode() ;

        head.next = tail ;
        tail.prev = head ;
    }

    public int get(int key){
        DLinkedNode node  = cache.get(key) ;

        if ( node == null ) {
            return -1 ;
        }

        moveToHead(node);
        return node.value;
    }

    public void put( int key , int value){
        DLinkedNode node = cache.get(key);

        if (node == null) {
            DLinkedNode newNode = new DLinkedNode(key ,value);
            cache.put(key , newNode) ;
            addToHead(newNode);
            size ++ ;
            if ( size > capacity ) {
                DLinkedNode tail = removeTail();
                cache.remove(tail.key);
                size -- ;
            }
        } else {
            node.value = value ;
            moveToHead(node) ;
        }
    }

    private void addToHead(DLinkedNode node) {
        node.prev = head ;
        node.next = head.next ;
        head.next.prev = node ;
        head.next = node ;
    }

    private void removeNode(DLinkedNode node ){
        node.prev.next = node.next ;
        node.next.prev = node.prev ;
    }

    private void moveToHead(DLinkedNode node) {
        removeNode(node);
        addToHead(node);
    }

    private DLinkedNode removeTail(){
        DLinkedNode res = tail.prev ;
        removeNode(res);
        return res ;
    }
}

/**
 * Your LRUCache object will be instantiated and called as such:
 * LRUCache obj = new LRUCache(capacity);
 * int param_1 = obj.get(key);
 * obj.put(key,value);
 */
```