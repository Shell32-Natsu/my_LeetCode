#Find Peak Element

[Find Peak Element](https://leetcode.com/problems/find-peak-element/ "Find Peak Element")

二分搜索，每次比较找到的num[mid]与邻居的大小来决定向哪边搜索,注意对于边界的处理,下标不能越界.

C++:

    class Solution {
    public:
        int findPeakElement(const vector<int> &num) {
            if(num.size() == 1) return 0;
            if(num.size() == 2) return num[0] > num[1] ? 0 : 1;
            int start = 0, end = num.size(), mid;
            while(start < end){
                mid = (start + end) / 2;
                if(mid == 0) return num[0] > num[1] ? 0 : 1;
                if(mid == num.size() - 1) return num[num.size() - 2] > num[num.size() - 1] ? num.size() - 2 : num.size() - 1;
                if(num[mid] > num[mid - 1] && num[mid] > num[mid + 1]){
                    return mid;
                }else if(num[mid] > num[mid - 1] && num[mid + 1] > num[mid]){
                    start = mid + 1;
                }else{
                    end = mid;
                }
            }
            return start;
        }
    };