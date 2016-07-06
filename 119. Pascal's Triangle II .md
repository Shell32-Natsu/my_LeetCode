#Pascal's Triangle II 

[Pascal's Triangle II](https://leetcode.com/problems/pascals-triangle-ii/ "Pascal's Triangle II")

杨辉三角，没什么好说的。题目要求能否用O(k)的额外空间。我的代码里用了两个vector，最大的大小为k+(k-1)=2k-1。

C++:

    class Solution {
    public:
        vector<int> getRow(int rowIndex) {
            vector<int> ret = {1};
            vector<int> last = {1};
            for(int i = 1; i <= rowIndex; i++){
                ret.clear();
                ret.push_back(last[0]);
                auto j = last.begin() + 1;
                for(; j != last.end(); j++){
                    ret.push_back(*j + *(j - 1));
                }
                ret.push_back(*(j - 1));
                last = ret;
            }
            
            return ret;
        }
    };