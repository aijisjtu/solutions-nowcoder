[TOC]

#### py

```python
from os import RWF_SYNC
import sys

for line in sys.stdin:
    a = line.split()
orgn=set()
for i in range(1,len(a)):
    orgn.add(int(a[i]))
natural=set()
for i in range(len(a)):
    natural.add(i)
ans=''.join(map(str, natural-orgn))
print(ans)
```

##### py 等效语法

注意：

```python
my_set = {1, 2, 3}
str_element = str([x for x in my_set][0])
```

```python
my_set = {1, 2, 3}
str_element = str(next(iter(my_set)))
```

####cpp

```cpp
#include <iostream>
#include <set>
#include <vector>
using namespace std;

int main() {
    vector<int> a;
    int num;

    while (cin >> num) {
        a.push_back(num);
    }

    set<int> orgn;
    for (int i = 1; i < a.size(); ++i) {
        orgn.insert(a[i]);
    }

    set<int> natural;
    for (int i = 0; i < a.size(); ++i) {
        natural.insert(i);
    }

    string ans;
    for (int num : natural) {
        if (orgn.find(num) == orgn.end()) {
            ans += to_string(num);
        }
    }

    cout << ans << endl;

    return 0;
}
```

####java

```java
import java.util.Scanner;

// 注意类名必须为 Main, 不要有任何 package xxx 信息
import java.util.HashSet;
import java.util.Scanner;
import java.util.Set;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Set<Integer> orgn = new HashSet<>();

        // Reading input from stdin
        while (scanner.hasNextInt()) {
            orgn.add(scanner.nextInt());
        }

        Set<Integer> natural = new HashSet<>();
        for (int i = 0; i < orgn.size(); ++i) {
            natural.add(i);
        }

        StringBuilder ans = new StringBuilder();
        for (int num : natural) {
            if (!orgn.contains(num)) {
                ans.append(num);
            }
        }

        System.out.println(ans.toString());
    }
}
```
