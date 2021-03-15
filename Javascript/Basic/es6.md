

## Set 和 Map的数据结构
### Set
> 方法( add, delete, has, clear, keys, values, entries, forEach )
* 它类似于数组，但是成员的值都是唯一的，没有重复的值。
### WeakSet
> 方法( add, has, delete )
* WeakSet 的成员只能是对象，而不能是其他类型的值。
### Map 
* 它类似于对象，也是键值对的集合，但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键。也就是说，Object 结构提供了“字符串—值”的对应，Map 结构提供了“值—值”的对应，是一种更完善的 Hash 结构实现

### WeakMap
* WeakMap只接受对象作为键名（null除外），不接受其他类型的值作为键名