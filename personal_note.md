---
image: /assets/img/note.jpg
menu: true
order: 6
---

# Personal_Note
> There are some note for myself.

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



### Trie树(前缀树)
> 储存字符串的一种数据结构  



