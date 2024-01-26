[TOC]

### py

```python
import sys

for line in sys.stdin:
    a = line.split()
max_val=abs(int(a[0]))
def min_steps_to_x_dp(x):
    dp = [float('inf')] * (max_val + 2)  # 初始化dp数组，初始值为无穷大
    dp[0] = 0  # 初始位置步数为0

    for i in range(1, x + 1):
        # 尝试三种走法
        if i % 2 == 0:
            dp[i] = min(dp[i - 1],  dp[i // 2]) + 1  # 使劲跳跃到当前点的两倍
        else:
            dp[i] = min(dp[i - 1],  dp[(i + 1)//2]+1) + 1  # 向后走一步

    return dp[max_val]
print(min_steps_to_x_dp(max_val))
```

### cpp

```cpp
#include<bits/stdc++.h>
using namespace std;
int main(){
    int n;
    cin>>n;
    n=abs(n);//正数和负数情况相同
    int dp[n+1];
    dp[0]=0;
    dp[1]=1;
    for(int i=2;i<=n;i++){
        if(i%2==0){
            dp[i]=min(dp[i-1]+1,dp[i/2]+1);//当n为偶数，两种情况到达n-1，n/2
        }else{
            dp[i]=min(dp[i-1],dp[(i+1)/2]+1)+1;//当n为奇数，两种情况，n-1，或者是（n+1)/2-1步
        }                                      //这一步解释为，到达n+1偶数步，然后在后退一步
    }
    cout<<dp[n]<<endl;
    return 0;

```

### java

#### under construction
