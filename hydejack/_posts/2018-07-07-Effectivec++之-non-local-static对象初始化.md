---
layout: post
title: Effectivec++之 non-local static对象初始化
author: author1
description: >
    什么是 non-local static 对象？？通俗来说， local对象  ——> 有域限制的对象， 比如一个命名空间内，一个块内等等。（受作用域限制）
---

**什么是 non-local static 对象？？通俗来说** 
>
local对象  ——> 有域限制的对象， 比如一个命名空间内，一个块内等等。           （受作用域限制）
non-local 对象 ——> 整个程序结束对象才，比如全局变量                          （不受作用域限制）
static 存在与 date区或者bbs区的对象才被收回， 不是stack变量， heap变量等等。  (直到程序完整结束才被收回)
综上所述， non-loacl static 变量就是  不受作用域限制 且  为static 的对象

举例子
```c++
//a.cpp
    class hen
    {
    Public:
        size_t make_eggs( );
    }
```

```c++
hen ji;//这是一个 non-local static 变量
//b.cpp

extern hen ji;

class eggs
{
public:
    void eggs()
    {
        ji.make_egg();
    }
}
```

ok, 我现在调用这个egg函数


```c++
// main.cpp

#include "a.cpp"
#include "b.cpp"
int main()
{
    eggs   a；
}
```

那么 a要被构造必须要 ji先被构造， 不然会很可怕。

但是， c++并没有规定在main中，不同  .cpp文件的编译顺序，所以怎么办呢？？？


**解决方法**
用 local static 变量 代替 non-local static 变量

```c++
//a.cpp

class hen
{
Public:
    size_t make_eggs( );
}

hen& chicken()
{
    static hen ji;
    return  ji;
}
```

```c++
//b.cpp


class eggs
{
public:
    void eggs()
    {
        chicken().make_egg();
    }
}

eggs& egg()
{
    static egg a
    return a;
}
```


ok, 我现在调用这个egg函数

```c++
// main.cpp

#include "a.cpp"
#include "b.cpp"
int main()
{
    eggs   egg()；
}
```

这样就可以避免 未编译对象的发生， 为什么呢？？？

**分析：**

从 main() 调用 eggs对象，

non-local static 的做法  ——>   调用 eggs 构造函数  ——> 调用 ji.make_egg() ——> 发现 ji对象没有被初始化 —>死亡

local static         的做法  ——> 调用  eggs() ——> 调用 egg 构造函数 ——> 调用 ji() ——> 调用 ji 的构造函数 —> 成功

可以看到，由于函数的存在， 第二种方法在对象再没有被初始化的条件下会被 执行初始化操作， 而 第一种却不会。



**缺陷**
如果对象 A 的初始化依赖于 B， 而 B 能否初始化又取决于 A 是否进行初始化。那么只能去 手动初始化（头疼）

