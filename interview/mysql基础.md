### 数据库索引的最左匹配原则如果不是按照顺序的那么有问题吗？
没有问题，因为mysql会进行优化，保证使用到索引
在使用explain的时候，我们其实可以发现索引有两种类型
index：只要判断条件在一个组合索引中，那么就可以使用到这个索引，这个索引一般不是组合索引的第一个参数
ref：这个代表真正使用到了索引

### 组合索引是怎么创建的？
首先按照第一个字段排序，然后再按照第二个字段进行排序，依次类推
