[TOC]

### 思路

- 取差值最大的
- 减数在被减数前面

遍历整个数组, A[i]作为被减数, i 之前最小的数作为减数

### cpp

```cpp
class Solution {
  public:
    /**
     * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
     *
     *
     * @param A int整型vector
     * @param n int整型
     * @return int整型
     */
    int Getmax (int a, int b){
        return a>b? a:b;
    }
        int Getmin (int a, int b){
        return a>b? b:a;
    }
    int getDis(vector<int>& A, int n) {
        // write code here
        int max = 0; // 结果最小为0
        int min = A[0]; // 默认最小为第一位
        for (int i = 1 ; i < n; i ++) {
            min = Getmin(A[i], min); // 第一位与遍历的比较, 取小的
            max = Getmax(A[i] - min, max); // A[i]减去之前最小的A[i], 取最大的
        }
        return max;

    }
};
```
