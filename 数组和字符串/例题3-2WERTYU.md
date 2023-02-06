__P47__

先考虑处理输入以及是否需要存储，存储的话用什么数据类型来存储\
发现可以边读入边输出所以不需要存储，处理输入可用%c\
接下来考虑除空格外的字符的变换，键盘上的字符是固定的可以用常量数组去存储，读入一个字符的时候只需要输出它的前一位就行了

```C++
#include <cstdio>
#include <cstring>

const char s[] = "`1234567890-=QWERTYUIOP[]\\ASDFGHJKL;'ZXCVBNM,./'";
int main(void)
{
	char c;
	
	while((c=getchar())!=EOF)
	{
		if(c==' '||c=='\n') putchar(c);
		else putchar(*(strchr(s,c)-1));
	}
	
	return 0;
}
```
