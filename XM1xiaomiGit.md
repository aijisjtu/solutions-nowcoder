[TOC]

## 小米 Git

- [原题链接](https://www.nowcoder.com/questionTerminal/4fcd94851d9142458329fd1d3e5802a8)

### 题目描述

Git 是一个常用的分布式代码管理工具，Git 通过树的形式记录文件的更改历史（例如示例图），树上的每个节点表示一个版本分支，工程师经常需要找到两个分支的最近的分割点。
例如示例图中 3,4 版本的分割点是 1。3,5 版本的分割点是 0。
给定一个用邻接矩阵 matrix 表示的树，请你找到版本 versionA 和 versionB 最近的分割点并返回编号。

注意： 1.矩阵中从第一行 （视为节点 0 ）开始，表示与其他每个点的连接情况，例如 [01011,10100,01000,10000,10000] 表示节点 0 与节点 1 ， 3 ， 4 相连，节点 1 与节点 0 ， 2 相连，其他点的以此类推。

2.并不保证是一棵二叉树，即一个节点有可能有多个后继节点，我们把节点 0 视为树的根节点。

数据范围：树上节点数量满足 1≤n≤100

- 示例 1
  输入
  `["01011","10100","01000","10000","10000"],1,2`
  输出
  `1`
- 示例 2
  输入
  `["0"],0,0`
  输出
  `0`

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
