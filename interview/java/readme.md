### String能被继承吗
不能，因为他被final修饰

### String底层如何实现 不可变的好处 采用了什么设计模式 字符串常量池
1.8 private final char value[]   
1.9 private final byte value[] 原因是有些字母不需要两个字节
有利于哈希值存储，线程安全，字符串常量池
采用了享元模式

字符串常量池在jdk1.7时被从方法区的运行时常量池移到了堆中的字符串常量池，我们在使用字面量（String s = "string"）创建字符串对象时，
会先在常量池进行查找，如果找到了直接将地址付给s，如果没有找到，那么就会进行创建然后放到常量池中；使用new（String s = new String("string")）
进行创建字符串对象时，也会先在字符串常量池中进行查找，如果找到了，那么会在堆上复制一份副本，然后将堆上的地址赋值给s，如果没有找到那么
会先在常量池中进行创建，然后再进行复制副本到堆上，再赋值给s
总之就是先去查找常量池，先放到常量池

### 基本类型的常量池
整型（包括能自动转成整型的类型）在[-128,127]之间时会使用到常量池

### System.out.print(5+""+10+5)
输出5105，在字符左边的数字会进行计算，在字符串之后就会进行拼接

### switch可以支持哪些参数
在1.7之前只支持int以及可以转换成int的类型，在之后支持了String

### Object有哪些方法
getClass equals hashcode clone wait notify notifyAll finalize toString

### 构造方法可以被哪些修饰
四种修饰类型都可以，但是static final abstract 不可以，而且不可以有返回值

### lambda表达式的优缺点
简洁，调用快
函数是编程，丧失了可读性

### 多态定义 实现机制
在编译期和运行期的类型不一致
重写和重载

### 管理文件和目录的类是什么
File createFile delete isFile exists listFiles isDiractory mkdir getName getPath

### a+=b 和a=a+b的区别
前者会进行强转，后者不会，有可能会报错

### long能不能进行强转成double
不能，可以相反

### 基本类型是如何进行自动转型的
（byte short char）->int ->long->double <-float

### byte数组如何转成String
new String(byte,"utf-8")

### final修饰的变量运算时会不会进行强转
不会

### java可以用哪些进行命名变量
数字 字母 下划线 $ 数字不能开头

### 一个java文件里有多个接口，那么会生成多少个class文件
有多少个接口就会生成多少个class文件

### stream和reader、writer的区别
stream是字节流
reader、writer是字符流

### jdbc使用了什么模式
桥接模式
