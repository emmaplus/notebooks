## 哪些数据类型可以称为集合Collection呢?

Array Object  Map Set 这些都是集合类型的数据结构 , 下面分别介绍一下这几种数据类型

### Array

常见

### Map

Map 和 Object的区别 
  
1. Object有property

2. object的key只能是string类型，而map可以是任意类型

3. 可以很容易获取map的size

### Set

类似数组，但是成员的值都是唯一的，没有重复的值。可以作为给array去除的一种方法

### WeakSet

类似Set，也是不重复的值的集合。它与Set的有两个区别：

1. WeakSet 的成员只能是对象，即引用类型的值

2. WeakSet中的成员都是弱引用，即垃圾回收机制不考虑WeakSet对该对象的引用，这意味着无法引用WeakSet的成员，WeakSet也不可遍历。它还没有size属性

#### 那WeakSet的作用是什么呢？

WeakSet的一个用处，是储存DOM节点，而不用担心这些节点从文档移除时，会引用内存泄露