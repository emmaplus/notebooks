# 高级性能

人们会担心state每次改变时所有的子components都重新渲染的机制会带来性能的损耗, 但是React采用了很多聪明的技巧来最小化更新UI时的操作Dom的性能损耗.

## Immutable-js 与shouldComponentUpdate 的使用

Immutable-js 的三大特点:

* Immutable 即一旦创建,它的值永远不会改变

* Persistent 从现有的collection中创建一个新的collection,新旧collection都是可访问的

* Structural Sharing 如果collection改变,则会创建一个不同引用的collection,新collection拥有和原collection一样的数据结构,相反地,如果新collection和原collection一样则原collection会直接返回.

Immutable-js给我们提供了一种性能消耗低的对比object变化的方式,这可以结合shouldComponentUpdate来提升性

### PureRenderMixin

PureRenderMixin 是指相同的props和state只有一种render结果, 假如props里有个object,它内部发生了改变,但是object本身并未改变,这种情况下re-rendering会再次发生,这就不符合pure的概念.

props和state使用Immutable objects则符合pure render