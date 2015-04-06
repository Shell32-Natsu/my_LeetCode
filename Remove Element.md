#Remove Element

[Remove Element](https://leetcode.com/problems/remove-element/ "Remove Element")

使用vector来移除元素，应该算是偷懒了吧= =。

C++:

    class Solution {
    public:
        int removeElement(int A[], int n, int elem) {
            vector<int> v(A, A + n);
            sort(v.begin(), v.end());
            auto i = v.begin();
            for(; i != v.end() && *i != elem; i++);
            if(i == v.end())return n;
            
            auto j = i;
            for(; j != v.end() && *j == elem; j++);
            v.erase(i, j);
            int ret_len = v.size();
            for(int i = 0; i < ret_len; i++)
                A[i] = v[i];
            return ret_len;
        }
    };