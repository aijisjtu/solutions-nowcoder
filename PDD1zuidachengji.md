### 思路

最大值只能出现在以下两种情况的较大值:<br>

1. 最大的 3 个正数的乘积（包括全是负数的情况，应是最大的 3 个数的乘积）
2. 最小的 2 个负数\*最大的正数的乘积

所以找出最大三个正数和最小的两个负数这 5 个数即可
但是这道题要求时间复杂度 o(n)，但是空间复杂度 o(1)
如果先把所有数存到数组中，然后排序找出这 5 个数，那么空间复杂度为 o(n)
所以不能将全部数存到数组再排序，只能在输入的过程中就把最大的三个数和最小的两个数存起来，最后比较最大值的组合即可

### py

注意，这不满足空间复杂度$O(1)$的要求。

```python
import sys

n = int(sys.stdin.readline().strip())
if n < 3:
    print(0)
    exit()
data = list(map(int, sys.stdin.readline().strip().split()))
data.sort()
print(max(data[-1] * data[-2] * data[-3], data[-1] * data[0] * data[1]))


```

### cpp

```cpp
#include<iostream>
#include<limits.h>
using namespace std;
int main() {
    int i, n, num;
    long long max_mul;
    /* max1, max2, max3 分别为最大值，次大值，第三大值
     * min1, min2 分别为最小值，次小值*/
    long long max1, max2, max3, min1, min2;
    max1 = max2 = max3 = INT_MIN;
    min1 = min2 = INT_MAX;
    cin >> n;
    for (i = 0; i < n; i++) {
        cin >> num;
        if (num < min1) {
            min2 = min1;
            min1 = num;
        } else if (num < min2) {
            min2 = num;
        }

        if (num > max1) {
            max3 = max2;
            max2 = max1;
            max1 = num;
        } else if (num > max2) {
            max3 = max2;
            max2 = num;
        } else if (num > max3) {
            max3 = num;
        }
    }
    max_mul = max1 * max2 * max3 > max1 * min1 * min2 ? max1 * max2 * max3 : max1 *
              min1 * min2;
    cout << max_mul << endl;
    return 0;
}
```
