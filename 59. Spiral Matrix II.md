#Spiral Matrix II

[Spiral Matrix II](https://leetcode.com/problems/spiral-matrix-ii/ "Spiral Matrix II")

螺旋输出序列。

C++:

    class Solution {
    public:
        vector<vector<int> > generateMatrix(int n) {
            vector<vector<int> > ret(n);
            for(int i = 0; i < n; i++)
                ret[i].resize(n);
            if(n == 0)return ret;
            int a = 1;
            for(int i = n; i > 0; i-=2){
                if(i == 1 && n % 2 == 1){
                    ret[(n - i) / 2][(n - i) / 2] = a++;
                    break;
                }
                for(int j = (n - i) / 2; j < n - (n - i) / 2 - 1; j++)
                    ret[(n - i) / 2][j] = a++;
                for(int j = (n - i) / 2; j < n - (n - i) / 2 - 1; j++)
                    ret[j][n - (n - i) / 2 - 1] = a++;
                for(int j = n - (n - i) / 2 - 1; j > (n - i) / 2; j--)
                    ret[n - (n - i) / 2 - 1][j] = a++;
                for(int j = n - (n - i) / 2 - 1; j > (n - i) / 2; j--)
                    ret[j][(n - i) / 2] = a++;
            }
            
            return ret;
        }
    };