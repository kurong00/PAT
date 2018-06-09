### 题目描述

> The task is simple: given any positive integer N, you are supposed to count the total number of 1's in the decimal form of the integers from 1 to N. For example, given N being 12, there are five 1's in 1, 10, 11, and 12.

### 输入描述

> Each input file contains one test case which gives the positive N (<=2^30).

### 输出描述:
> For each test case, print the number of 1's in one line.

### 输入例子
> 12

### 输出例子
> 5



## 题目解析
时间限制只有100ms显然是需要找出数学规律： 
|| current | high  | low  |a|
| :---: |:--:| :---:| :---:|:--:|
| 作用| 当前位的数 | current左边的所有高位 |代表current右边的所有低位|当前位（如1，10，100等等）

规律是当current为：
|| 0 | 1  | >=2  |
| :---: |:--:| :---:| :---:|
| 规律| 1的个数只由高位决定：=高位的数 x 当前位，例如12034，假设当前位是百位0，则1的个数为12 * 100=1200个 | 1的个数由高位和低位共同决定：=高位的数 x 当前位+低位的数+1，例如12134，假设当前位是百位1，则1的个数为12 * 100 + 34 + 1 |1的个数只由高位决定：=(高位的数 + 1) x 当前位，例如12345，则1的个数为( 12 + 1 ) * 100 = 1300个

```C++
#include <iostream>
using namespace std;
int main() {
	int n, a = 1, high = 0, low = 0, current = 0, result = 0;
	cin >> n;
	while (n / a)
	{
		high = n / (a * 10);
		current = n / a % 10;
		low = n % a;
		if (current == 0)
			result += a * high;
		else if (current == 1)
			result += a * high + low + 1;
		else
			result += a * (high + 1);
		a *= 10;
	}
	cout << result;
	return 0;
}
```