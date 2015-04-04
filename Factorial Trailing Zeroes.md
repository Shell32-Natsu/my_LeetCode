#Factorial Trailing Zeroes

[Factorial Trailing Zeroes](https://leetcode.com/problems/factorial-trailing-zeroes/ "Factorial Trailing Zeroes")

统计结果中因子5的个数。

C/C++:

    int ret = 0;
    while(n > 0){
        ret += n / 5;
        n /= 5;
    }
    return ret;

Python:

    class Solution:
        # @return an integer
        def trailingZeroes(self, n):
            ret = 0
            while(n > 0):
                ret = ret + n / 5;
                n = n / 5;
                
            return ret