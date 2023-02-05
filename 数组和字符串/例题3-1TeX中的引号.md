__P45__

在TeX中，左双引号是“``”，右双引号是“''”。输入一篇包含双引号的文章，你的任务是转换成TeX的格式

如何处理输入？(%c  %s还是字符串函数)是否需要存储？\
根据输入输出先考虑读取单个字符，发现可以边读边输出，然后只需要一个标志变量就可以区分是左右引号
```C++
#include <cstdio>

int main(void)
{
	char c;
	int flag = 0;
	char *s[2] = {"``","''"};
	
	while(scanf("%c",&c)!=EOF)
	{
		if(c=='"')
		{
			printf("%s",s[flag]);
			flag = !flag;
		}else printf("%c",c);
	}
	
	return 0;
}
```
