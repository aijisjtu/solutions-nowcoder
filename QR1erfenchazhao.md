### 思路

[https://www.acwing.com/blog/content/195/](https://www.acwing.com/blog/content/195/)

求最小的`i`，使得`a[i]=key`，若不存在，则返回`-1`

先确定一个风格：循环条件总是`l<r`，总是返回`l`

### py

```python


def BinarySearch(A, n, val):
    l,r=0,n-1
    while(l<r):
        m=l+((r-l)>>1)
        if val>A[m]:
            l=m+1
        else:
            r=m
    if (A[l]==val):
        return l
    return -1

while True:
    try:
        l=input()
        A = l[0]
        n = l[1]
        val = l[2]
        print(BinarySearch(A, n, val))
    except:
       break
```

### cpp

```cpp

class BinarySearch {
  public:
    int getPos(vector<int> a, int n, int val) {
    int m,l=0,r=n-1;//闭区间[0,n-1]
    while(l<r){
        m=l+((r-l)>>1);//向下取整
        if(a[m]<val)l=m+1;//是向下取整的，右移一个不会越界
        else r=m;//如果相等，继续查左边区间
    }
    if(a[r]==val)return r;
    return -1;
    }
};
```

### 变式

求最大的`i`，使得`a[i]=key`，若不存在，则返回`-1`

```cpp
int search2(int a[],int n,int key){
    int m,l=0,r=n-1;//闭区间[0,n-1]
    while(l<r){
        m=l+((r+1-l)>>1);//向上取整
        if(a[m]<=key)l=m;//向上取整的，如果右移一个会越界
        //如果相等，继续查右边区间
        else r=m-1;
    }
    if(a[l]==key)return l;
    return -1;
}
```
