__P20__

输出所有形如aabb的4位完全平方数

直观的思路从1100到9988循环遍历，如果开方后是整数则可以输出，判断是整数，开方再平方可判断。\
考虑到题目的特殊性，完全可以不用遍历将近一万次，根据aabb的特征，可判断a的范围是1-9，b的范围是0-9，aa可以乘以1100实现，bb可以乘以11实现\
```C
#include <cstdio>
#include <cmath>

int main(void)
{
	int sum, tmp;
	
	for(int a=1;a<=9;a++)
	{
		for(int b=0;b<=9;b++)
		{
			 sum = a*1100+b*11;
			 tmp = 	(int)sqrt(sum*0.1);
			 if(tmp*tmp==sum)
			 	printf("%d\n",sum);
		} 
	}
	
	return 0;
}
```
浮点数的存储以及运算可能存在误差，1可能存为0.9999...，一种解决办法是改成四舍五入
```C++
#include <cstdio>
#include <cmath>

int main(void)
{
	int sum, tmp;
	
	for(int a=1;a<=9;a++)
	{
		for(int b=0;b<=9;b++)
		{
			 sum = a*1100+b*11;
			 tmp = floor(sqrt(sum)+0.5);
			 if(tmp*tmp==sum)
			 	printf("%d\n",sum);
		} 
	}
	
	return 0;
}
```
还有一种方法是枚举平方根，避开开平方操作
```C++
#include <cstdio>
#include <cmath>

int main(void)
{
	int x;
	
	for(x=30;;x++)
	{
		int n = x*x;
		if(n>9999) break;
		int a = n/100;
		int b = n%100;
		if(a/10==a%10 && b/10==b%10)
			printf("%d\n",n);
	}
	
	return 0;
}
```
