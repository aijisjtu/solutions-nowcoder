[TOC]

### 思路

因为是 2x+1 或者 2x+2，所以 22 娘扭蛋的结果是奇数，33 娘扭蛋的结果是偶数;
这样只要一步步倒推就可以了;

### python

```python
import sys

def func(N):
    res = ""
    while(N != 0):
        if N%2 == 0:
            res = "3"+res
            N = (N-2)/2
        else:
            res = "2"+res
            N = (N-1)/2
    return res

for line in sys.stdin:
    a = line.rstrip()
    res = func(int(a))
    print(res)
```

### CPP

```cpp
#include<stdio.h>

int main()
{
    int N,x=0,i=0;
    int a[1024]={0};
    scanf("%d",&N);
    while(1)
    {
        if(N % 2 == 0)
        {
            N=(N-2)/2;
            a[i]=3;
        }
        else
        {
            N = (N-1)/2;
            a[i]=2;
        }
        if(N == 0)break;
        i++;
    }
    for(;i>=0;i--)
    {
        printf("%d",a[i]);
    }
    return 0;
}
```

### java

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args){
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        StringBuilder s = new StringBuilder();
        while (n > 0) {
            if(n % 2 == 0){
                s.insert(0, "3");
                n = (n - 2) / 2;
            }else{
                s.insert(0, "2");
                n = (n - 1) / 2;
            }
        }
        System.out.println(s);
    }
}
```
