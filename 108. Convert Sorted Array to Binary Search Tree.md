#Convert Sorted Array to Binary Search Tree

[Convert Sorted Array to Binary Search Tree](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/ "Convert Sorted Array to Binary Search Tree")

排序数组转换为平衡二叉搜索树。先用递归算法。

C++:

    class Solution {
    public:
        TreeNode *sortedArrayToBST(vector<int> &num) {
            if(num.size() == 0)return NULL;
            
            TreeNode *root = new TreeNode(num[num.size() / 2]);
            vector<int> left_tree(num.begin(), num.begin() + num.size() / 2);
            vector<int> right_tree(num.begin() + num.size() / 2 + 1, num.end());
            
            root->left = sortedArrayToBST(left_tree);
            root->right = sortedArrayToBST(right_tree);
            
            return root;
        }
    };