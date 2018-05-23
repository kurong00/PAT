### 题目描述

> Given three integers A, B and C in 
$$[2^{64} , (-2)^{64} ]$$  
> you are supposed to tell whether A+B > C.

### 输入描述

> The first line of the input gives the positive number of test cases, T (<=10). Then T test cases follow, each consists of a single line containing three integers A, B and C, separated by single spaces.

### 输出描述:
> For each test case, output in one line "Case #X: true" if A+B&gtC, or "Case #X: false" otherwise, where X is the case number (starting from 1).

### 输入例子
> 3
>
>1 2 3
>
>2 3 4
>
>9223372036854775807 -9223372036854775808 0

### 输出例子
>Case #1: false
>
>Case #2: true
>
>Case #3: false

## 题目解析
注意取值范围:     
$$ A,B,C\in[ 2^{64} , (-2)^{64} ]$$ 
因此当A > 0, B > 0时，sum可能会溢出。sum范围为
  $$\in[ 0,2^{64} ]$$
溢出得到的结果应该是
$$\in[ (-2)^{64},-2 ]$$
所以 sum < 0时候说明上溢出了，因此这种情况为false。

反之sum下溢出了，这种情况也为false
```C++
#include<iostream>
using namespace std;
int main()
{
	int n;
	cin >> n;
	long long a, b, c, sum;
	for (int i = 1; i <= n; i++) {
		cin >> a >> b >> c;
		sum = a + b;
		if (a > 0 && b > 0 && sum <= 0)
			cout << "Case #" << i << ": true" << endl;
		else if (a < 0 && b < 0 && sum >= 0)
			cout << "Case #" << i << ": false" << endl;
		else if (sum > c)
			cout << "Case #" << i << ": true" << endl;
		else
			cout << "Case #" << i << ": false" << endl;
	}
	return 0;
}
```