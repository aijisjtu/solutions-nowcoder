###递归

```cpp
class GrayCode {
public:
    vector<string> getGray(int n) {
        // write code here
        vector<string> res;
        string tmp = "";
        for(int i=0;i<n;i++){
            tmp += "0";
        }
        res.emplace_back(tmp);
        for(int i=1;i<=n;i++){
            //对称开始位置
            int idx = pow(2,i-1);
            for(int j = 1;j<=idx;j++){
                //反着取res的值，再加入到res中
                tmp = res[idx-j];
                tmp[n-i] = '1';
                res.emplace_back(tmp);
            }
        }
        return res;
    }
};
```