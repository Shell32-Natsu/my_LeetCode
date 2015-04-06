#Search Insert Position

[Search Insert Position](https://leetcode.com/problems/search-insert-position/ "Search Insert Position")

线性遍历C++:

    class Solution {
    public:
        int searchInsert(int A[], int n, int target) {
            int i;
            for(i = 0; i < n && A[i] < target; i++);
            return i;
        }
    };

时间12ms。

二分查找C++:

    class Solution {
    public:
        int searchInsert(int A[], int n, int target) {
            int low = 0, high = n;
            while(low < high){
                if(A[(low + high) / 2] == target) return (low + high) / 2;
                else if(A[(low + high) / 2] < target){
                    low = (low + high) / 2 + 1;
                }else{
                    high = (low + high) / 2;
                }
            }
            if(low == n)return low;
            if(A[low] < target)return low + 1;
            if(A[low] > target)return low;
        }
    };

时间8ms。
