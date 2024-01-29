###py

```python
import sys

for line in sys.stdin:
    a = line.split()
    print(int(a[0]) + int(a[1]))
# 变体
for line in sys.stdin:
    a = line.rstrip()
    res = func(int(a))
    print(res)

n = int(sys.stdin.readline().strip())
if n < 3:
    print(0)
    exit()
data = list(map(int, sys.stdin.readline().strip().split()))
data.sort()
print(max(data[-1] * data[-2] * data[-3], data[-1] * data[0] * data[1]))

# [1,3,5,7,9],5,3
while True:
    try:
        l=input()
        A = l[0]
        n = l[1]
        val = l[2]
        print(BinarySearch(A, n, val))
    except:
       break


while True:
    try:
        l = list(map(int, input().split()))
        r, x, y, x1, y1 = l[:]
        print("%.0f" % s(r, x, y, x1, y1))
    except:
        break

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
int main() {
    int a, b;
    while (cin >> a >> b) { // 注意 while 处理多个 case
        cout << a + b << endl;
    }
}

include<vector>
int main(){
    int n;
    cin >> n;
    vector<int> arr;
    arr.resize(n);

    for(int i=0; i<n; ++i){
        cin >> arr[i];
    }

}
```
