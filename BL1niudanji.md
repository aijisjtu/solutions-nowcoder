[TOC]

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

### CPP 略

### java 略
