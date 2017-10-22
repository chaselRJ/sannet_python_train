# collections

collections是Python内建的一个集合模块，提供了许多有用的集合类。

## namedtuple

```
import collections
Point = collections.namedtuple('Point', ['x', 'y'])
p = Point(1, 2)
print(p.x)
print(p.y)
```

`namedtuple`是一个函数，它用来创建一个自定义的`tuple`对象，并且规定了`tuple`元素的个数，并且可以使用属性而不是索引来访问元素。

## OrderDict

默认的dict在插入元素的时候，其保存顺序与插入顺序没有任何关系。

```python
In [3]: a = {}

In [4]: a['name'] = 'xx'

In [5]: a['age'] = 24

In [6]: a['sex'] = 'male'

In [7]: a
Out[7]: {'age': 24, 'name': 'xx', 'sex': 'male'}
```

OrderedDict类能够维持字典插入的顺序。

```python
In [8]: import collections

In [9]: d = collections.OrderedDict()

In [10]: d['name'] = 'xx'

In [11]: d['age'] = 24

In [12]: d['sex'] = 'male'

In [13]: d
Out[13]: OrderedDict([('name', 'xx'), ('age', 24), ('sex', 'male')])
```

`OrderdDict`内部维护着一个根据键插入顺序排序的双向链表。每次当一个新的元素插入进来的时候，它会被放到链表的尾部。

需要注意的是，一个 `OrderdDict` 的大小是一个普通字典的两倍，因为它内部维护着另外一个链表。
