# 高级性能

人们会担心state每次改变时所有的子components都重新渲染的机制会带来性能的损耗, 但是React采用了很多聪明的技巧来最小化更新UI时的操作Dom的性能损耗.

## Immutable-js 与shouldComponentUpdate 的使用

Immutable-js 的三大特点:

* Immutable 即一旦创建,就不能再被更改

* Persistent Data Structure(持久化数据结构) 使用旧数据创建新数据时,要保证旧数据同时可用且不变.

* Structural Sharing (结构共享) 即如果对象树中一个节点发生变化,只修改这个节点和受影响的父节点,其他节点则进行共享.它会尽量复用内存

Immutable-js给我们提供了一种性能消耗低的对比object变化的方式,这可以结合shouldComponentUpdate来提升性

### PureRenderMixin

PureRenderMixin 是指相同的props和state只有一种render结果, 假如props里有个object,它内部发生了改变,但是object本身并未改变,这种情况下re-rendering会再次发生,这就不符合pure的概念.

props和state使用Immutable objects则符合pure render

关键词:_ClojureScript_, _Elm_, _函数式编程_, _TypeScript_