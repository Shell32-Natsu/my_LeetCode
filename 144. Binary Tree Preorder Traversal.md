#Binary Tree Preorder Traversal

[Binary Tree Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal/ "Binary Tree Preorder Traversal")

输出前序遍历序列，用迭代的方法。我的代码中为了方便使用右子树->左子树->根的顺序保存路径，最后倒过来就可以得到前序遍历。

C++:

    class Solution {
    public:
        vector<int> preorderTraversal(TreeNode *root) {
            vector<TreeNode*> path;
            vector<TreeNode*> ret;
            vector<int> r;
            if(root == NULL) return r;
            TreeNode *node = root;
            do{
                path.push_back(node);
                node = node->right;
            }while(node != NULL);
    
            while(!path.empty()){
    
                node = path[path.size() - 1];
                
                if(node->right != NULL){
                    path.push_back(node->right);
                    continue;
                }
                
                if(node->left != NULL){
                    path.push_back(node->left);
                    continue;
                }
    
    
                if(node->left == NULL && node->right == NULL){
                    path.pop_back();
                    ret.push_back(node);
                    if(path.size() == 0) break;
                    TreeNode *temp = path[path.size() - 1];
    
                    if((temp->right == node))
                        temp->right = NULL;
                    else if((temp->left == node)){
                        temp->left = NULL;
                    }
    
                }
            }
    
            for(int i = ret.size() - 1; i >= 0; i--)
                r.push_back(ret[i]->val);
    
            return r;
        }
    };