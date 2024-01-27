[TOC]
### cpp
```cpp
#include "bits/stdc++.h"
using namespace std;
const int maxn=1e3+10;
int T,n;
int a[maxn];
struct node{
    int l,r;
}p[maxn];
int main()
{
    scanf("%d",&T);
    while(T--){
        scanf("%d",&n);
        memset(a,0,sizeof(a));
        memset(p,0,sizeof(p));
        for(int i=1;i<=n;i++) scanf("%d",&a[i]);
        for(int i=2;i<=n;i++){
            p[i-1].l=min(a[i-1],a[i]);
            p[i-1].r=max(a[i-1],a[i]);
        }
        --n;
        int flag=0;
        for(int i=1;i<=n;i++){
            for(int j=1;j<i;j++){
                if((p[j].l<p[i].r&&p[j].l>p[i].l&&p[j].r>p[i].r)||(p[j].r<p[i].r&&p[j].r>p[i].l&&p[j].l<p[i].l)){
                    flag=1; 
                    break;
                }
            }
            if(flag) break;
        }
        if(!flag) printf("n\n");
        else printf("y\n");
    }
    return 0;
}
```
### java
```java
import java.util.*;
public class Main{
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        int T = in.nextInt();
        while (T-- > 0){
            int n = in.nextInt();//端点数
            int[] arr = new int[n];
            for (int i = 0; i < n; i++) {//输入端点
                arr[i] = in.nextInt();
            }
            List<int[]> cir = new ArrayList<>();
            for (int i = 0; i < n - 1; i++) {//储存圆
                int left = Math.min(arr[i],arr[i + 1]);//左端点
                int right = Math.max(arr[i],arr[i + 1]);//右端点
                cir.add(new int[]{left,right});
            }
            //题意为所有的圆都不存在相交，才返回false
            boolean flag = false;
            for (int i = 1; i < cir.size(); i++) {
                for (int j = 0; j < i; j++) {
                    //先设置两个圆的端点
                    int left1 = cir.get(i)[0],right1 = cir.get(i)[1];//圆1的端点
                    int left2 = cir.get(j)[0],right2 = cir.get(j)[1];//圆2的端点
                    //两圆相交的情况
                    if (left1 < left2 && right1 < right2 && right1 > left2){
                        flag = true;
                        break;
                    }else if (left1 > left2 && left1 < right2 && right1 > right2){
                        flag = true;
                        break;
                    }
                }
            }
            if (flag){
                System.out.println("y");
            }else {
                System.out.println("n");
            }
        }
    }
}
```