[TOC]

### 朴素解法

#### py

```python
class Solution:
    def Typing(self , s ):
        strng=""
        for i in s:
            if i=='<':
                if strng!="":
                    strng=strng[0:-1]
            else:
                strng+=i
        return strng
```

### 第二种解法

####py

```python
class Solution:
    def Typing(self,s):
        r = ""
        del_cnt = 0
        for i in range(len(s)-1, -1, -1):
            if s[i] == '<':
                del_cnt += 1
            elif del_cnt == 0:
                r = s[i]+r
            elif del_cnt != 0:
                del_cnt -= 1
        return r
```

#### cpp

```CPP
#include <string>
class Solution {
public:
    string Typing(string s) {
        // write code here
        string ans;
        int del_cnt=0;
        for(int i=s.length()-1;i>=0;i--) {
            if(s[i]=='<')del_cnt++;
            else if (del_cnt)del_cnt--;
            else ans=s[i]+ans;
        }
        return ans;
    }
};
```

#### java

```java
import java.util.*;
public class Solution {
    public String Typing (String s) {
        String ans = "";
        int delCnt = 0;
        for (int i = s.length() - 1; i >= 0; i--) {
            if (s.charAt(i) == '<') {
                delCnt++;
            } else if (delCnt > 0) {
                delCnt--;
            } else {
                ans = s.charAt(i) + ans;
            }
        }

        return ans;
    }
}
```
