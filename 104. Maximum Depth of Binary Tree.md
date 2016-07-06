#Maximum Depth of Binary Tree

[Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/ "Maximum Depth of Binary Tree")

递归计算左右子树的高度。

C++:

    class Solution {
    public:
        int maxDepth(TreeNode *root) {
            if(root == NULL) return 0;
            int left_depth = 1, right_depth = 1;
            if(root->left != NULL)
                left_depth = maxDepth(root->left) + 1;
            if(root->right != NULL)
                right_depth = maxDepth(root->right) + 1;
                
            return left_depth > right_depth ? left_depth : right_depth;
        }
    };