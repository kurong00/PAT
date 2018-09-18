### 题目描述

> Given any string of N (>=5) characters, you are asked to form the characters into the shape of U. For example, "helloworld" can be printed as:
>
>h&#160;&#160;&#160;&#160;&#160;d
>
>e&#160;&#160;&#160;&#160;&#160;l
>
>l&#160;&#160;&#160;&#160;&#160;r
>
>lowo
>
>That is, the characters must be printed in the original order, starting top-down from the left vertical line with n~1~ characters, then left to right along the bottom line with n~2~ characters, and finally bottom-up along the vertical line with n~3~ characters. And more, we would like U to be as squared as possible -- that is, it must be satisfied that n~1~ = n~3~ = max { k| k <= n~2~ for all 3 <= n~2~ <= N } with n~1~n~2~ + n~3~ - 2 = N.

### 输入描述

> Each input file contains one test case. Each case contains one string with no less than 5 and no more than 80 characters in a line. The string contains no white space.

### 输出描述:
> For each test case, print the input string in the shape of U as specified in the description.

### 输入例子
> helloworld!

### 输出例子
>
>h&#160;&#160;&#160;&#160;&#160;!
>
>e&#160;&#160;&#160;&#160;&#160;d
>
>l&#160;&#160;&#160;&#160;&#160;l
>
>lowor
>

## 题目解析
唯一需要注意的点是行n1，列n2的计算方式
```C++
    int n1 = (n + 2) / 3;
    int n2 = n + 2 - n1 * 2;
```

```C++
#include<iostream>
#include<string>
using namespace std;
int main()
{
	string s;
	cin >> s;
	int n = s.length();
	int n1 = (n + 2) / 3, n2 = n + 2 - n1 * 2;
	for (int i = 0; i < n1 - 1; i++) {
		cout << s[i];
		for (int j = 0; j < n2 - 2; j++) {
			cout << " ";
		}
		cout << s[n - 1 - i];
		cout << endl;
	}
	for (int i = n1 - 1; i < n1 + n2 - 1; i++)
		cout << s[i];
	return 0;
}

```