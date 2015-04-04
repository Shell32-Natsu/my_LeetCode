#Rotate Array

[Rotate Array](https://leetcode.com/problems/rotate-array/ "Rotate Array")

使用另一个数组进行保存。

C++:

    class Solution {
    public:
        void rotate(int nums[], int n, int k) {
            k = k % n;
            int t_arr[n];
            int i,j = 0;
            for(i = n - k;i < n;i++)
                t_arr[j++] = nums[i];
            for(i = 0;i < n - k;i++)
                t_arr[j++] = nums[i];
            for(i = 0;i < n;i++)
                nums[i] = t_arr[i];
        }
    };