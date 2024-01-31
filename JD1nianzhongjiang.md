### cpp

```cpp
class Bonus {
  public:
    int getMost(vector<vector<int> > board) {
        // write code here
        int length = board.size();
        int width = board[0].size();
        vector<vector<int>> gifts(length, vector<int>(width, 0));
        gifts[0][0] = board[0][0];
        for (int i = 0; i < length; i++) {
            for (int j = 0; j < width; j++) {
                if (i == 0 && j == 0) //情况1
                    continue;
                else if (i == 0) //情况2
                    gifts[i][j] = gifts[i][j - 1] + board[i][j];
                else if (j == 0) //情况3
                    gifts[i][j] = gifts[i - 1][j] + board[i][j];
                else//正常情况
                    gifts[i][j] = max(gifts[i - 1][j], gifts[i][j - 1]) + board[i][j];
            }
        }

        return gifts[length - 1][width - 1]; //返回到右下角的礼物价值值总和


    }
};
```
