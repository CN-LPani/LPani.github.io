---
title: 2021Python学习笔记
date: 2022-02-06
tags: [Python,计算机,学习]
katex: true
copyright: true
cover: https://jsd.cdn.zzko.cn/gh/CN-LPani/tu@main/2021Python学习笔记/2021python学习笔记.3orupxd9tem0.jpg
---
## **print函数**

#### 数字

（如520，98.5）输出时不用引号

如`print(520)`和`print(98.5)`

也可以用引号 `print("520")`

<br/>

#### 字符串

必须加引号

如`print("hello world")`

<br/>

#### 含有运算符的表达式

像$1+3$

其中1和3是操作数，加号是运算符，含有两者叫做表达式

如`print(3+1)` 那么它就输出4

<br/>

#### 输出到本地()

如`open("E:/日你妈.txt","a+")`

- 其中`a`如果在`E:/`目录下没有`日你妈.txt`这个文件就创建一个，
  
  如果有就在原来基础上追加
  
  (读写的方式创建文件。没同名文件创建，有的话在文件内容后面追加)

现在我们输入`open("E:/日你妈.txt","a+")`

然后把它们存入变量`F`中

相当于`F=open("E:/日你妈.txt","a+")`

再把内容写入`日你妈.txt`中

输入`print("haha",file=F)`

其中file ：文件路径

最后还可以把这个变量关掉

输入`F.close()`

```python
F = open("E:/日你妈.txt","a+")
print("haha",file=F)
F.close()
```

<br/>

#### 不换行输出

如`print("hello","world","python")`

<br/>

## 一些转义字符

`\n `     换行（`n`指的是newline）

`\r`       回车

`\t  `     水平制表符

`\b `      退格

其中 \ 是转义功能的首字母

输入`print("hello\nworld")`

那么它就会输出
`hello`
`world`

输入`print("hello\tworld")`

那么它就会输出

`hello    world`

就是一组四个空格的位置

具体了解[Python教程全套完全入门版转义字符与原字符](https://www.bilibili.com/video/BV1Sw411Z779?p=7&t=159.6)

输入`print("hello\rworld")`

那么它就会输出

`world`

直接把hello覆盖掉了

<br/>

> 在输入`print("https:\\www.baidu.com")`时

> 它会只输出`https:\www.baidu.com`
> 
> 这时候要多加一个或两个<u>反斜杠</u>
> 
> 因为它把第二个反斜杠看成了转义字符首字母，就自动隐藏了

<br/>

## **原字符**

<u>不希望字符串中的转义字符起作用，就使用原字符</u>

假如我们输入`print("hello\nworld")`

那么它就会输出

`hello`

`world`

那么我们想要让`\n`不起作用，让它输出`hello\nworld`

就在`"hello\nworld"`前加R或r，即`print(R"hello\nworld")`或`print(r"hello\nworld")`

- 注意：原字符最后一个字符不能是<u>反斜杠</u>
  > 如`print(r"hello\nworld\")`
  > 
  > 那么它就会报错了
  > 
  > 要非要输出hello\nworld\的话，
  > 
  > 输入`print(r"hello\nworld\")`
  > 
  > 也就是在后面加一个空格
  > 
  > 总之就是想办法不要把反斜杠和后面的引号接触在一起
  > 
  > 因为反斜杠会把引号转成<u>原字符</u>造成格式错误

<br/>

## **二进制与字符编码**

<u>什么叫做二进制和字符编码</u>

[Python教程全套完全入门版二进制与字符编码](https://www.bilibili.com/video/BV1Sw411Z779?p=8&t=42.4)

一个位置可以写上0或1

设有a个位置，那就有$$2^a$$个位置

<img src="https://jsd.cdn.zzko.cn/gh/CN-LPani/tu@main/2021Python学习笔记/379f9d9eaab32674b12e2dc0cd08dc3e.6yoca5is8ng0.jpg" alt="无标题.png" style="zoom:110%;" />

- 8个位置（$2^8$=256）称为1字节（即8bit=1bite）
- 1024bite=1KB(千字节)
- 1024KB=1MB（兆字节）
- 1024MB=1GB（吉字节）
- 1024GB=1TB(太字节)
  
  <br/>
  
  <u>各种字符编码</u>
  
  ![截图](https://jsd.cdn.zzko.cn/gh/CN-LPani/tu@main/2021Python学习笔记/a0e6c63540f1466725becd0d849e68b3.scw3ehox6q8.jpg)

#### chr函数

`乘`十六进制是4e58，那么它的二进制是`0100111001011000`

1. 输入`print(chr())`
2. 再把`0100111001011000`丢进去，即`print(chr(0100111001011000))`
   > 但发现它会报错，因为它是二进制，而<u>它默认的是十进制</u>
   > 
   > 这时候再在`0100111001011000`前输入个0b
   > 
   > 即`print(chr(0b0100111001011000))`
   > 
   > 它就会输出`乘`

<br/>

#### ord函数

1. 输入`print(ord(”“))`
2. 再把`乘`丢进去，即`print(ord("乘"))`，那么它就会输出`20056`
   > `20056`是十进制，它默认的是十进制

<br/>

- 注意：chr函数括号内<u>不用加引号</u>，ord函括号内<u>要加引号</u>
- 不管是几进制，转到计算机中都是二进制，因为计算机只识别二进制
- chr函数不仅能搞二进制，还能搞八进制等各种进制，如`print(chr(20056))`

<br/>

## 保留字

在Python中<u>不可以给对象命名</u>的单词，

如你在给新的Python文件命名时或设置变量时不可以使用

#### 怎么查询保留字

输入

```python
import keyword
print(keyword.kwlist)
```

那么它就会输出所有的保留字

<br/>

#### **标识符**

在<u>给对象起的名字</u>叫做标识符

<u>规则如下</u>

- 你可以使用字母、数字、下划线
- 不能以数字开头
- 不能是保留字
- 我是严格区分大小写的

<br/>

## **变量**

变量是内存中一个<u>带标签的盒子</u>

![截图](https://jsd.cdn.zzko.cn/gh/CN-LPani/tu@main/2021Python学习笔记/4a8d7ba6255458e24b9e80588b6f2df4.31t5dtucryo0.jpg)

把`马丽亚`放进变量里

输入`name="马丽亚"`

其中name即变量名（标识符），可在标识符原则下随便取

`"马丽亚"`是字符串

![截图](https://jsd.cdn.zzko.cn/gh/CN-LPani/tu@main/2021Python学习笔记/0ca45b24d3caef8b5efc2b9f40f68c17.3ykne84umq80.jpg)

<br/>

#### 变量的定义和使用

变量由<u>标识、类型和值</u>三部分组成

- 标识：表示对象<u>所存储的内存地址</u>，使用内置函数`id(obj)`来获取  
- 类型：表示的是对象的<u>数据类型</u>，使用内置函数`type(obj)`来获取 
- 值：表示对象<u>所存储的具体数据</u>（即刚才的`马丽亚`）, 使用`print(obj)`可以将值进行打印输出
  
  <br/>

#### 如何获取标识、类型和值

先了解一点

- `id`是标识
- `type`是类型
- 值的话就直接输出变量，即`print（name）`，输入`print(value(name))`会报错

先将`马丽亚`存入`name`中，输入`name="马丽亚"`

输入`print(id(name))`

输出的就是这个变量在内存中的地址

输入`print(type(name))`

输出的就是这个变量的数据类型，即`<class 'str'>`，那么这个变量数据类型是`str`

输入`print(name)`

输出的就是这个变量中的值

```python
name="马丽亚"
print(id(name))
print(type(name))
print(name)
```

<br/>

#### **变量的多次赋值**

当我们输入

```python
name="马丽亚"
name="楚溜冰"
```

时

再输入`print(name)` 它就会输出`楚溜冰`

那`马丽亚`就不会被使用，将会被视为内存垃圾，

Python的垃圾回收机制会对这个垃圾进行一个回收

![截图](https://jsd.cdn.zzko.cn/gh/CN-LPani/tu@main/2021Python学习笔记/8ff0e394fb9cec25bfa1d85ececdfc74.as9dbyqrg3s.jpg)

<br/>

## **常见的数据类型**

- int     整数类型         如98（不带小数点和引号的）
- float  浮点数类型       如3.14159、9.8、5.6、33.9
- bool  布尔类型    只能取两个值，这两个值就是`true`或者`false`，用来表示<u>真</u>或者<u>假</u>
- str     字符串类型      只要加上引号的就称为字符串类型，如"hello world"

<br/>

#### 整数类型（integer，简写为int）

英文为integer, 简写为int, 可以表示<u>正数、负数和零</u>，但<u>绝对不能有小数点和引号</u>

> 整数的不同进制表示方式
> 
> - 十进制→默认的进制 
> - 二进制→以`0b`开头 
> - 八进制→以`0o`开头
> - 十六进制→`0x`开头
> 
> ![截图](https://jsd.cdn.zzko.cn/gh/CN-LPani/tu@main/2021Python学习笔记/aad19126b424eee043564f5d4b26b5da.76o5ga5806g0.jpg)

1. 把随意一些整数类型存入变量当中，如输入`n1=98` `n2=56` `n3=22`（设置多个变量）
2. 输入`print(type(n1),type(n2),type(n3))`，输出的都是int，即整数类型

```python
n1=98
n2=56
n3=22
print(type(n1),type(n2),type(n3))
```

将<u>二进制、十进制、八进制、十六进制</u>转换成<u>十进制</u>

输入`print(118)`（十进制）

那么它就会输出`118`（十进制）

输入`print(0b1010110)`（二进制）

那么它就输出`86`（十进制）

输入`print(0o55555)`（八进制）

那么它就会输出`23405`（十进制）

输入`print(0x4e58)`（十六进制）

那么它就会输出`20056`（十进制）

```python
print(118)
print(0b1010110)
print(0o55555)
print(0x4e58)
```

<br/>

#### 浮点数类型

包括<u>整数和小数</u>部分，如3.141596535、33.56、2.33

> 输入
> 
> ```python
> a=3.14
> print(type(a))
> ```
> 
> 时
> 
> 它输出的是`<class 'float'>`，即浮点数类型

- 浮点数存储<u>不精确性</u>  
  
  使用浮点数进行计算时，可能会出现<u>小数位数不确定</u>的情况

正常状态下我们输入`print(1.1+1.1)`

那么它就会输出`2.2`

那当我们输入`print(1.1+2.2)`时，理论上是`3.3`

但它输出`3.3000000000000003`

这说明<u>个别</u>浮点数不能精确存储

<u>任何语言中浮点数都不能精确存储</u>

> 解决方案
> 
> 导入模块<u>decimal</u>再去计算
> 
> ```python
> from decimal import Decimal
> print(Decimal("1.1")+Decimal("2.2"))
> ```
> 
> 结果输出的就是`3.3`

<br/>

#### 布尔类型（bool，全称Boolean）

用来表示<u>真或假</u>的值 

True 表示真，False 表示假

- True表示整数1
- False表示整数0

输入

```python
b=True
c=False
print(type(b),type(c))
```

它就会输出`<class 'bool'> <class 'bool'>`，即布尔类型

> 转成整数计算
> 
> 如输入
> 
> ```python
> print(True+1)
> print(False+1)
> ```
> 
> 那么它就会输出
> 
> ```python
> 2
> 1
> ```
> 
> 就相当于把`True`和`False`分别当成1和2看

<br/>

#### 字符串类型

- 字符串又被称为<u>不可变的字符序列</u>
- 可以使用<u>单引号、双引号或三引号</u>来定义
- 单引号和双引号定义的字符串<u>必须在一行</u>
- 三引号定义的字符串可以<u>分布在连续的多行</u>

```python
#单引号
print('hello world')
#双引号
print("hello world")
#三引号
print("""hello
world""")
```

其中三引号像这样输入那么它输出的就是

```python
hello
world
```

- 三引号有两种召唤方式
  
  按三下双引号，即`""""""`
  
  按三下单引号，即`''''''`
  
  例如
  ```python
  #输入
  print("""hello
  world""")
  print('''hello
  world''')
  ```
  ```python
  #输出
  hello
  world
  hello
  world
  ```

<br/>

#### **数据类型转换**

- 为什么需要数据类型转换？
  
  将不同数据类型的数据拼接在一起

举个例子

我想让它输出`我叫 楚溜冰 我今年 20 岁了`

直接输入

```python
name="楚溜冰"
age=20
print(type(name),type(age))
print("我叫",name,"我今年",age,"岁了")
```

还有一种方法，通过加号（连接符）连接（把逗号换成了加号）

```python
name="楚溜冰"
age=20
print(type(name),type(age))
print("我叫"+name+"我今年"+age+"岁了")
```

但是它会报错（TypeError: can only concatenate str (not "int") to str）

意思是str和int格式不能连接在一起（name和age）

- <u>解决方案</u>如下
  
  将int类型通过`str()`转换成str类型
  
  `print("我叫"+name+"我今年"+str(age)+"岁了")`
  
  也就是在`age`前加个`str`，再用括号括起来
  
  输出的内容为`我叫楚溜冰我今年20岁了`

用连接符和用逗号的区别是前者没有空格，后者有空格

<br/>

#### 数据类型转换函数

`str()`将其它数据类型转换成str，即字符串

`int()`将其它数据类型转换成int，即整数

`float()`将其它数据类型转换成float，即浮点数

![截图](https://jsd.cdn.zzko.cn/gh/CN-LPani/tu@main/2021Python学习笔记/f035d0f603f2414512801d9f5ddb44cc.3zkakt6d01g0.jpg)

<br/>

## 计算

➕       加法

➖       减法

✳       乘法

/           除法

**         幂运算（例如2✳✳3=2的3次方=2✖2✖2=8）

%         1.取余     （一正一负要公式），例如9%4=1
 2.余数=被除数-除数*商，例如9%(-4)=-3       9-(-4)✳(-3)=-3

//         整除（例如9➗4=2.25，那么9整除4就是2，抹掉了小数点和小数后面的数）

整除：一正一负往下取整。例如9➗-4得出来是-2.25，整除后是-3，如下图

![无标题.png](https://jsd.cdn.zzko.cn/gh/CN-LPani/tu@main/2021Python学习笔记/f67c1cdf6adcbe3411f604bd4733aa0c.7e6qarv7fi40.jpg)
