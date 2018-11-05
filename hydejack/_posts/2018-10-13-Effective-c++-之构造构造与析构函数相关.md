--- 
layout: post
title: Effectivec++之 non-local static对象初始化
author: author1
description: >
&emsp; c++中，构造函数与析构函数是非常有用以及非常重要的.
---
#### 不要让 析构函数 抛出异常
```
&emsp;解决方法: 给用户写一个 close() 函数, 让用户手动结束有可能抛出异常的部分
```
<br>
<br>
#### 不要在 构造函数 或者 析构函数 中调用 virtual 函数
&emsp;子类调用构造函数会调用父类构造函数，且父类构造函数


