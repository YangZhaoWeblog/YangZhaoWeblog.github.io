--- 
layout: post
title: 2018-10-09-Effectivec++之-const成员函数
author: author1
description: > 
1. const成员函数不会 **直接** 修改对象内容
2. const对象只能调用 常成员 函数(最重要之处)
---
> 说明：常成员函数不能更新类的成员变量，也不能调用该类中没有用const修饰的成员函数(除非进行强制性转换)，只能调用常成员函数。

**特别注意**: 可以通过指针在 常成员函数中修改 其指向对象的值。而不会报错(因为是间接)
> 所以得出以下结论: 
<br>

#### 避免 const 与 non-const 成员函数的重复
> “调用 cosnt 成员函数来实现 non-const 成员函数
eg:
```c++
class example
{
	private:
		static char* a = "Hello world";
	public:
		char& = 
}
```

#### 编译器只要求不能直接修改对象， 但实际编程中， 我们也要做到让其不能间接修改
