[TOC]
###cpp

```cpp
#include <iostream>
#include <vector>
using namespace std;

int getMax(int a, int b){

    return a>b? a:b;

}

int main(){

    int n;
    cin >> n;
    vector<int> arr;
    arr.resize(n);

    for(int i=0; i<n; ++i){
        cin >> arr[i];
    }

    int sum = arr[0];
    int maxSum = arr[0];
    for(int i=1; i<n; ++i){
        sum = getMax(arr[i], sum+arr[i]);
        if(sum > maxSum){
           maxSum = sum;
        }
    }
    cout << maxSum;
    return 0;
}
```
