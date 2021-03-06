# Python笔记

## 数据类型
1. 浮点数可以直接使用e表示，123e-2
2. 字符串单引号双引号都可以，转义字符\
3. 布尔值True,False，首字母大写
4. 布尔运算and,or,not
5. 空值None
6. 引用赋值
7. 整数和浮点数没有大小限制，浮点数可能会表示为inf（无限大）

## 编码问题
- 计算机内存，服务器都使用Unicode编码，保存或传输、输出到网页时，都会转换为UTF-8编码
- Python3使用Unicode编码
- ord('A')  >>  65
- chr(65)  >>  'A'
- encode和decode方法
- len()获取字符数或字节数
- 格式化输出
```
>>  'Hi, %s, you have $%d.' % ('Michael', 1000000)
>>  'Hi, Michael, you have $1000000.'
```
- %d %f %s %x   整数 浮点数 字符串 十六进制数
- %s会把任何数据类型转换为字符串
- 使用%转义%，'%%'  >>  '%'
- 也可以使用format进行格式化
```
>>  'Hello, {0}, 成绩提升了 {1:.1f}%'.format('小明', 17.125)  
>>  'Hello, 小明, 成绩提升了 17.1%'
```

## 集合/数组（list和tuple）
#### list
1. 有序集合，使用中括号和逗号分割
2. 也可以使用len（）获取数组大小
3. 使用中括号和索引来访问元素list[0]，索引可以为负，list[-1]==list[len(list)-1]
4. 使用append(object)方法向队尾加入元素，insert(i,object)方法向位置i插入元素
5. 使用pop()方法删除队尾元素，pop(i)方法删除位置i的元素
6. list元素的数据类型可以不同

#### tuple
1. 有序列表，使用圆括号和逗号分割

## 条件
1. 使用if，else和elif关键字
2. 判断条件直接写，使用：（冒号）结尾，内部代码使用缩进
``` python
if age >= 18:
   print('adult')
elif age >= 6:
   print('teenager')
else:
   print('kid')
 ```
## 循环
1. for循环形式``` for x in xs: ```
2. range(n)函数虎生成一个从0开始到n-1的整数序列
3. while循环形式``` while 条件: ```
4. break和continue语句可使用

## 字典dict(map)和集合set
1. 形式``` {'Michael': 95, 'Bob': 75, 'Tracy': 85}```使用大括号和逗号分隔，调用时使用中括号，添加键值对是也直接使用中括号。关键词`dict`
2. 可以使用get(key)方法获取value或指定value（两个参数）
3. 使用pop(key)方法删除
> list和dict比较          
 dict:        
    查找和插入速度极快，不会随着key的增加而变慢      
    需要占用大量内存，内存浪费多      
 list:      
      查找和插入的时间随元素的增加而增加        
      占用空间少，内存浪费少

4. 形式```set([2, 3, 4])```
5. set是无序的，不重复的，可以做交集（&），并集（|）等操作
6. set也是使用大括号的{}，新建集合时使用set()而不是{}（新建了字典）
7. 使用.add()方法添加元素，.update()也可
8. 使用.remove()（删除不存在的元素会报错）删除元素，或.discard()（不会报错）

## 函数
1. 内置类型转换函数int(),float(),str(),bool()
2. 使用def语句定义函数```def 函数名（参数名）：函数内容```
3. 空语句pass
4. 检查传入的参数类型
```python
if not isinstance(x, (int, float)):
   raise TypeError('bad operand type')
```
5. 返回多个值用逗号分割，实际上是一个tuple
6. 默认/可选参数——在定义函数时给该参数一个默认值（age=2），该参数就变为可选参数
7. 有默认参数时应按顺序输入，不过也可直接指定（age=4），此时不限制输入顺序（尤其是有多个默认参数时）
8. 默认参数的值仅在参数定义时创建一次，若使用可变对象（如list），则参数会发生改变
9. 可变参数——传入参数个数可变，使用*（*args），实际上还是一个tuple
10. 使用\*也可以将list或tuple作为可变参数（*list）
11. 关键字参数——相当于dict，使用**（**kw)
12. 参数中可以直接传入任意个数的键值对（键不需要加引号），在函数中会形成一个名为kw的字典
13. 使用**dict将字典dict变为关键字参数
14. 命名关键字参数——限制关键字参数的名字，只用时之前必须有一个*
15. 与普通参数不同，命名关键字参数调用时必须使用键值对的方式指明参数名

## 高级特性
#### 切片
1. 使用冒号（:）进行切片
2. 示例```list[1:6]```复制list的第1到6个元素，  ```list[1:6:2]```每2个元素取一个，   ```'asfdfg'[:3]```字符串，tuple都可以进行切片操作
3. 可以使用两个

#### 列表生成式
1. 用于生成列表
2. 可以是单层循环也可以是两层循环
```
>>  [m + n for m in 'ABC' for n in 'XYZ']  
>>  ['AX', 'AY', 'AZ', 'BX', 'BY', 'BZ', 'CX', 'CY', 'CZ']
```
3. 使用for···in···语句
4. for可以使用不只一个变量```for k, v in d.items()```

#### 生成器
1. generator，不会在创建的时候一次性生成，而是会在循环的过程中不断生成
2. 第一种创建方法——将列表生成式的[]换为()
3. 是可迭代对象，可直接使用for循环
4. 第二种创建方法——使用```yield```关键字
5. 如果一个函数定义中包含yield关键字，那么这个函数就不再是一个普通函数，而是一个generator。
6. 这里，最难理解的就是generator和函数的执行流程不一样。函数是顺序执行，遇到return语句或者最后一行函数语句就返回。而变成generator的函数，在每次调用next()的时候执行，遇到yield语句返回，再次执行时从上次返回的yield语句处继续执行。

#### 迭代器
1. 可以直接作用于for循环的数据类型统称为可迭代对象iterable
2. 可以被next()函数调用并不断返回下一个值的对象成为迭代器iterator
3. 可以使用isinstance()函数来判断是否为可迭代对象或是否为迭代器
4. 可以使用iter()函数从iterable类型的对象获得iterator对象
5. 迭代器(iterator)是一个数据流，是不能提前知道序列长度的有序序列，属于惰性计算。


## 函数式编程
1. 函数本身也可以赋给变量（赋值时只使用函数名，没有括号），这样变量就变成了一个函数
2. 变量可以指向函数，那么函数就可以作为另一个函数的参数（要求同上），产生所谓高阶函数
3. `map()`函数接受两个参数，一个是函数，一个是可迭代对象，map函数将传入的函数作用到可迭代对象的每个元素，并将结果作为iterator返回。
4. `reduce()`函数也接受两个参数，一个是函数（这个函数一定是必须接受两个参数的），一个是序列，reduce函数是将序列的第一个元素与第二个元素先做计算，然后将结果与第三个元素计算，持续进行直至最后一个元素，返回结果。
5. `filter()`函数用于过滤序列。filter()也接受两个参数，一个是函数，一个是可迭代对象，并将函数一次作用于每个元素，根据返回值是False还是True决定是丢弃还是保留该元素，并将结果作为iterator返回。
6. `sorted()`函数可以对list进行排序
7. sorted()函数还可以接收一个key函数，并将指定函数作用于list的每个元素上，根据key函数返回的结果进行排序
8. sorted()函数反向排序使用`reverse=True`实现
9. `返回函数`——将函数作为返回值返回，并且这个函数不会立即执行，会在再次调用时执行
10. `闭包`——相关参数和变量都保存在返回的函数中
11. `匿名函数`——不需要显式定义的函数
12. 关键字`lambda`表示匿名函数，冒汗前面的表示函数参数

##### 装饰器
- 不修改函数的定义，又可以在代码运行期间动态增加功能的方式，称之为`装饰器(decorator)`
- 本质上是一个返回函数的高阶函数。将待装饰的函数作为参数传入，将这个函数名作为标签至于函数定义前（@function）
- 不带参数的装饰器
```python
import functools

def log(func):
    @functools.wraps(func)
    def wrapper(*args, **kw):
        print('call %s():' % func.__name__)
        return func(*args, **kw)
    return wrapper

@log
def functionA(): 
##相当于functionA=log(functionA)
``` 
- 带参数的装饰器
```python
import functools

def log(text):
   def decorator(func):
      @functools.wrap(func)
      def wrapper(*args,**kw):
         print('%s  %s():' %(text, func.__name__))
         return func(*args, **kw)
      return wrapper
   return decorator
```

##### 偏函数
- 目的是将一个函数的某些参数值固定住（设置新的默认值），形成新的函数
-使用`functools.partial()`函数实现


## datetime模块
> datetime主要分为date,time,datetime,timedelta四个模块

### datetime
- `strptime(time_str,form_str)`——用于将指定格式日期字符串转换为datetime对象
- `strftime(form_str)`——用于指定格式输出
- 可以进行加减法和大小比较，基于时间戳。减法结果为timedetla对象

### date
- 直接使用`date(Y_int,m_int,d_int)`来指定日期
- `timetuple()`——获取date的struct_time对象，格式为元组


## 正则表达式
- `re.complie(pattern)`——将正则表达式模式编译成一个正则表达式对象
- `re.match([pattern,]string)`——在字符串首部进行匹配，匹配不到则返回none，返回一个可以使用span()的对象
- `re.search([pattern,]string)`——对整个字符创进行匹配，匹配不到返回none，同上
- `re.sub（pattern,repl,string[,count,flags]）`——对于输入的一个字符串，利用正则表达式，实现祖父穿替换处理，返回被替换后的字符串。`pattern`是正则表达式对象，`repl`是被替换的策略，可以是字符串，也可以是对被匹配到的字符串的处理函数，主义传输过去的是特殊对象，可以使用group的那种，`string`是原字符串，`count`是处理匹配字符串个数
- `re.findall(pattern,string)`——查找所有匹配，返回一个列表