#Plus One

[Plus One](https://leetcode.com/problems/plus-one/ "Plus One")

数组模拟计算。

C++:

    class Solution {
    public:
        vector<int> plusOne(vector<int> &digits) {
            vector<int> ret = digits;
            auto i = ret.end() - 1;
            if(*i < 9)(*i)++;
            else{
                if(ret.size() <= 1){
                    *i = 0;
                    ret.insert(ret.begin(),1);
                }else{
                    for(;i != ret.begin() && *i == 9; i--){
                        *i = 0;
                    }
                    if(i != ret.begin())(*i)++;
                    else{
                        if(*i < 9)(*i)++;
                        else{
                            *i = 0;
                            ret.insert(ret.begin(),1);
                        }
                    }
                }
            }
            return ret;
        }
    };