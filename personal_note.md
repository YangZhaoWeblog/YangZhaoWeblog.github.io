---
image: /assets/img/note.jpg
menu: true
order: 6
---

# Personal_Note
> There are some note for myself. Acm题是有板子的，但是大多数都是板子解决不了的，就是种种的变种s. 总的来说， **应当见多识广记住更多的变式**。
算法已经有好几个月没有练过了，现在回归训练，
1. 每天要5道算法题，
2. 做不完就去吃屎。
3. 每天推进 effectice c++ 一到二个条目
4. 闲了就看 linux 多线程服务端编程,并更新 STL 库
<br>
## 一.数论

### gcd算法
```c++
//已知 a, b 求最最大公因数c
int gcd(int a, int b)
{
	return !a?b:gcd(b%a, a);
}
```
```c++
//已知 a, b 求最小公倍数c
int lcm(int a, int b)
{
	return a/gcd(b%a, a)*b;
}
```
###### 变种
Hdu 2502
//已知 父亲a, 和最大公因数c, 求母亲 b
```c++
int a, c, b;
cin >> a >> c;
b = 2*c;
while( gcd(a, c) != b )
{
	b += c;
}

cout << b << endl;
```

## 二. 搜索

### 深度优先搜索
> 三要素:   
>    1.  返回条件
>    2.  状态转移方程

##### 汉诺塔
```c++
#include <iostream>
using namespace std;

int num;
void han(char a, char b, char c, int n)
{
    if(n != 0)
    {
        ++num;
        han( a, c, b, n-1);//把 n-1 个借助c 由 a 移动到 b
        printf("%c ——> %c\n", a, c);//把剩下一个盘子移动到 c
        han( b, a, c, n-1);//把 n-1 个借助a 由 b 移动到 c
    }
    return;
}

int main()
{
    int n;

    while(cin >> n)
    {
        num = 0;
        han('A', 'B', 'C', n); // 1 3 7 15 31 63 127 255 511 1023 2047 
        cout <<  num << endl;
    }
}
```
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 公式 :n ——> (2^n)-1   

###### 变种
Hdu 1207 ——> 4个棍子的移动

















<br>
<br>
### Trie树(前缀树)
> 储存字符串的一种数据结构  



```sql
create table book( bno nvarchar(255) , name nvarchar(255),
     price float,
     author nvarchar(255),
     publish nvarchar(255),
     publishdate datetime
     );



create table reader
     (
     rid nvarchar(255),
     name nvarchar(255),
     sex nvarchar(255),
     birthdate datetime
     );


create table borrow ( rid float,
     bno float,
     borrowdate datetime
     );
```
