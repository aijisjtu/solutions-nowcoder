[TOC]

### 思路

采用双指针的方法，我们分别用左右指针 l,r 表示左右数组的和，即左指针 l 表示的是区间[1,r]的和，右指针 r 表示的是区间[r,n]的和，然后左右指针进行移动，移动规则如下：
如果左数组的和大于右数组的和，右指针移动，同时记录右数组和，即 sumr+=a[r--]。
如果左数组的和小于右数组的和，左指针移动，同时记录左数组和，即 suml+=a[l++]。
如果左数组的和等于右数组的和，左右指针移动，同时记录答案和左右数组的和，即 sumr+=a[r--], suml+=a[l++]。
直至满足条件 l > r，退出循环。

复杂度分析：
时间复杂度：O(n)
空间复杂度：O(n)

### cpp

```cpp
#include <bits/stdc++.h>
using namespace std;
typedef long long LL;
const int MAXN = 2e5+5;
LL a[MAXN];
int main() {
 int n; cin>>n;
 for(int i=1; i<=n; i++) cin>>a[i];
 int l = 1, r = n;
 LL suml = a[l], sumr = a[r];
 LL ans = 0;
 while(l < r) {
     if(suml == sumr) {
         ans = suml;
         suml += a[++l];
         sumr += a[--r];
     }
     else if(suml > sumr) sumr += a[--r];
     else suml += a[++l];
 }
 cout<<ans<<endl;
 return 0;

}
```
