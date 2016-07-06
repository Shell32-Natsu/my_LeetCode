#Single Number

[Single Number](https://leetcode.com/problems/single-number/ "Single Number")

位运算，应该是最简单的一题了。

C:

    int singleNumber(int A[], int n) {
        unsigned ret = 0;
        for(int i = 0; i < n; i++){
            ret ^= A[i];
        }
        return ret;
    }