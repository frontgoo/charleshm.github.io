---
published: true
author: Charles
layout: post
title:  "字符串，向量，数组"
date:   2016-02-21 14:28
categories: 数据结构与算法
---

#### 命名空间
- 头文件不应包含 using 声明


----------


### 字符串

#### 初始化的几种方式
- 直接初始化：不使用等号
- 拷贝初始化：使用等号

{% highlight c++ %}
string s1               //默认初始化，s1是一个空串
string s2(s1)           //s2是s1的副本
string s2 = s1          //等价于s2(s1)，s2是s1的副本
string s3("value")      //s3是字面值"value"的副本
string s3 = "value"     //等价于s3("value")
string s4(n,'c')        //s4初始化为由连续n个字符c组成的串
{% endhighlight %}

- 对于一般的内建类型，这两种初始化基本上没有区别。 
- 当用于类类型对象时，初始化的复制形式和直接形式有所不同：直接初始化直接调用与实参匹配的构造函数，复制初始化总是调用复制构造函数。复制初始化首先使用指定构造函数创建一个临时对象，然后使用复制构造函数将那个临时对象复制到正在创建的对象。 


----------


#### 常用操作

{% highlight c++ %}
getline(is,s)
s.empty()
s.size()
{% endhighlight %}


----------


#### 字符串读取
> 在执行读取时（cin），string对象会自动忽略开头的**空白**（即空格符、换行符、制表符等），并从第一个真正的字符开始读取，直到遇到下一处**空白**为止

而 getline 从给定的输入流中读入内容，知道遇到**换行符**为止。只要一遇到换行符就结束读取并返回结果，哪怕一开始就是换行符也是如此，此时返回空 string


----------


#### 字面值和string对象相加
必须确保每个加法运算符的两侧运算对象至少有一个是string：

{% highlight c++ %}
string s4 = s1 + ","
string s5 = "Hello" + ",";  //错误，两个运算对象都不是string
{% endhighlight %}

> 为了与 C 兼容，所以 C++ 中的字符串字面值**并不是**标准库类型 string 对象。


----------


#### 基于范围的 for 语句

如果需要访问对象中的没一个元素，使用范围 for 语句会非常简洁。

{% highlight c++ %}
string str("some string");
for (auto c : str)
    cout << c << endl;
{% endhighlight %}


----------


### vector

vector 是模板而非类型，容纳着其它对象，所以常常被称作容器。

#### 初始化


----------


#### 添加元素

c++ 标准要求 vector 在运行时可以高效快速的添加元素，因此在定义 vector 对象时设定其大小也就没什么必要了。

{% highlight c++ %}
push_back()
{% endhighlight %}


----------


#### 迭代器
我们知道可以使用**下标**运算符来访问 string 和 vector 中的元素，c++ 中有一种更加通用的机制来达到相同的目的，**迭代器**。

{% highlight c++ %}
// b表示v的第一个元素，e表示v尾元素的下一位置
auto b = v.begin(), e = v.end(); 
{% endhighlight %}

> 如果容器为空，则 begin 和 end 返回的是同一迭代器，都是尾后迭代器。


----------


#### 迭代器支持的运算

{% highlight c++ %}
*iter         //返回迭代器iter所指元素的引用
iter->mem     //等价于 (*item).mem，为了简化而引入
++item        //令item指向容器中的下一个元素
--item        //令item指向容器中的上一个元素
item1 == item2
item1 != item2
{% endhighlight %}

> c++ 程序员都习惯性使用 != ，因为所有标准库容器的迭代器都定义了 == 和 !=，但是它们中的大多数都没有定义 < 运算符


----------


#### 迭代器类型
如果对象只需读而不需要写操作的话最好使用**常量类型**， cbegin 和 cend

{% highlight c++ %}
//begin,end
vector<int>::iterator it;
string::iterator it2;

//cbegin,cend
vector<int>::const_iterator it3;
string::const_iterator it4;
{% endhighlight %}