[TOC]

### 思路

计算两点之间直线距离，每步移动 2r 的距离，移动 x 步后有余数，则再移动一步即可，因为倒数两步可以按照三角移动，距离可以介于 r 到 2r 之间

### py

```python
import math


def s(r, x, y, x1, y1):
    d1 = (x1 - x) ** 2 + (y1 - y) ** 2
    d = math.sqrt(d1)
    if d % (2 * r) == 0:
        s1 = d // (2 * r)
    else:
        s1 = d // (2 * r) + 1
    return s1


while True:
    try:
        l = list(map(int, input().split()))
        r, x, y, x1, y1 = l[:]
        print("%.0f" % s(r, x, y, x1, y1))
    except:
        break
```
