[TOC]

最近公共祖先，还有递归的做法，以后碰到再说

### 思路

求最近公共祖先，先是把输入转换成一个树形结构，用字典存储：

然后使用深度优先递归查找目标节点，把经过的路径以列表记录下来。

然后两个节点的路径对比，找到最后的相同元素即为最近的公共祖先。

### py

```python
class Solution:
    def Git(self, matrix: List[str], versionA: int, versionB: int) -> int:

        global alist, blist
        alist = []  # 用来保存a的路径
        blist = []  # 用来保存b的路径
        tree = {}
        for i in range(len(matrix)):  # 整理为字典，树形结构
            tree[i] = []
            relation = list(matrix[i])
            index = 0
            while len(relation) > 0:
                r = relation.pop(0)
                if r == "1":
                    tree[i].append(index)
                index += 1

        def walk(tmplist, pre, node):
            tmplist.append(node)
            if node == versionA:  # 找到a，保存路径
                global alist
                alist = tmplist.copy()
            if node == versionB:  # 找到b，保存路径，注意这里a和b可能是同一个值，所以不要用else
                global blist
                blist = tmplist.copy()
            for i in tree[node]:  # 遍历执行下级节点
                if i == pre:  # 注意跳过来时的节点
                    continue
                walk(tmplist, node, i)
                tmplist.pop()

        walk([], 0, 0)
        res = 0
        while len(alist) > 0 and len(blist) > 0:  # 逐个弹出首位比较，直到不相同或者路径为空
            a = alist.pop(0)
            b = blist.pop(0)
            if a == b:
                res = a
            else:
                break
        return res
```

### java

```java
import java.util.*;


public class Solution {

    public void dfs(int node, int father, int dep, int[] path, int[] depth,String[] mat) {
        depth[node] = dep;
        path[node] = father;
        for (int i = 0; i < mat.length; i++) {
            if (i != father && mat[node].charAt(i)=='1') {
                dfs(i,node,dep+1,path,depth,mat);
            }
        }
    }
    public int Git(String[] matrix, int indexA, int indexB) {
        int n  = matrix.length;
        int[] depth = new int[n];
        int[] father = new int[n];
        father[0] = -1;
        dfs(0,-1,0,father,depth,matrix);
        while (depth[indexA] > depth[indexB]) {
            indexA = father[indexA];
        }
        while (depth[indexB] > depth[indexA]) {
            indexB = father[indexB];
        }
        while (indexA != indexB) {
            indexA = father[indexA];
            indexB = father[indexB];
        }
        return indexA;
    }
}
```
