### 1. 可以使用`哈希表`来减少查找数组的时间

> 待学习：14.最长公共前缀

# 2. 关于Stack
- 继承于Vector的栈，LIFO，拥有方法`push`——压栈,`pop`——出栈,`peek`——查看栈顶元素,`empty`——查询栈是否为空,`search`——查找元素（距离栈顶的距离，最短为1，不在栈中返回-1）

# 3. 关于Vector
- 同步的，线程安全的，不需要保证线程安全时可以使用ArrayList代替。返回的迭代器会尽量保证快速失败。                                     
- 继承AbstractList类，实现了List、、、接口
- 存在一个数组缓冲区作为此Vector的容量，大于等于实际数据量，在不够大时大小增长为原来的二倍
- 定义一个Vector时可以规定initialCapacity（Vector的初始容量，默认为10）和capacityIncrement（默认为0）（无参数不定义，一个参数，两个参数）
- `ensureCapacity(int minCapacity)`保证容量，将容量扩大为指定容量（如果原来小于此容量）

# 4. 关于快速失败fail-fast
> Java的一种错误检测机制，可以检测到集合在返回迭代器后进行的修改（如果此时继续使用该迭代器）并抛出ConcurrentModificationException异常（通常针对多线程，单线程也可能出现此错误）