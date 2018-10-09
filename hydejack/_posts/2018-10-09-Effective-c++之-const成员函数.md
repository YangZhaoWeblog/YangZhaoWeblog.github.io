--- 
layout: post
title: 2018-10-09-Effective-c++之-const成员函数
author: author1
description: > 
 尽可能的使用const
---
> 推论: 
 1. const成员函数不会 **直接** 修改对象内容
 2. const对象只能调用 常成员 函数(最重要之处)   
  说明：常成员函数不能更新类的成员变量，也不能调用该类中没有用const修饰的成员函数(除非进行强制性转换)，否则只能调用常成员函数。

<br>
**特别注意**: 可以通过指针在 常成员函数中修改 其指向对象的值。而不会报错(因为是间接)

<br>
#### 一. mutable 变量
	表示这些函数极其有可能被修改，即在 const 成员函数内(被间接修改)

<br>
#### 二. 避免 const 与 non-const 成员函数的重复
> “调用 cosnt 成员函数来实现 non-const 成员函数
<br>
```c++
class example
{
    string a = "0123456";
public:
    const char& get_five()const
    {
        //一系列复杂操作
        return a[5];
    }

    const char& get_five()
    {
        return
            const_cast<char&>
            (
                (static_cast<const example&>(*this)).get_five()
            );
    }
};
```

#### 编译器只要求不能直接修改对象， 但实际编程中， 我们也要做到让其不能间接修改
