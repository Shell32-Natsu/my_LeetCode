#Find Minimum in Rotated Sorted Array

[Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/ "Find Minimum in Rotated Sorted Array")

没有问题。

C++:

    class Solution {
    public:
        int findMin(vector<int> &num) {
            if(*num.begin() < *(num.end() - 1))return *num.begin();
            for(auto i = num.begin() + 1; i != num.end(); i++){
                if(*i < *(i - 1))return *i;
            }
            return *num.begin();
        }
    };