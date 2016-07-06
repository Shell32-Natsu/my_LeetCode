#Number of 1 Bits

[Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/ "Number of 1 Bits")

位运算，没有任何难度。这个程序用C比用C++快了3倍（4ms，12ms）。

C++:

    class Solution {
    public:
        int hammingWeight(uint32_t n){
            int ret = 0;
            while(n > 0){
                if(n & 1)
                    ret++;
                n = n >> 1;
            }
            
            return ret;
        }
    };