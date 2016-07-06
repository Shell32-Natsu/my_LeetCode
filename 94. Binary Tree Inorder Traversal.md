#Binary Tree Inorder Traversal

[Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/ "Binary Tree Inorder Traversal")

使用迭代得到中序遍历序列。

C++:

    class Solution {
    public:
        vector<int> inorderTraversal(TreeNode *root) {
            vector<TreeNode*> path;
            vector<TreeNode*> ret;
            vector<int> r;
            if(root == NULL) return r;
            TreeNode *node = root;
            do{
                path.push_back(node);
                node = node->left;
            }while(node != NULL);
    
            while(!path.empty()){
    
                node = path[path.size() - 1];
    
                if(node->left == NULL){
                    int i;
                    for(i = 0; i < ret.size() && ret[i] != node; i++);
                    if(i == ret.size())ret.push_back(node);
                }
    
                if(node->left != NULL){
                    path.push_back(node->left);
                    continue;
                }
    
                if(node->right != NULL){
                    path.push_back(node->right);
                    continue;
                }
    
                if(node->left == NULL && node->right == NULL){
                    path.pop_back();
                    if(path.size() == 0) break;
                    TreeNode *temp = path[path.size() - 1];
    
                    if((temp->right == node))
                        temp->right = NULL;
                    else if((temp->left == node)){
                        temp->left = NULL;
                    }
    
                }
            }
    
            for(int i = 0; i < ret.size(); i++)
                r.push_back(ret[i]->val);
    
            return r;
        }
    };