#Populating Next Right Pointers in Each Node

[Populating Next Right Pointers in Each Node](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/ "Populating Next Right Pointers in Each Node")

求每个节点的右边一个节点，用递归实现，效率不是很高，有时间再实现非递归算法。

C++:

    class Solution {
    public:
        void connect(TreeLinkNode *root, TreeLinkNode *parent = NULL) {
            if(root == NULL)return;
            if(parent != NULL){
                if(root == parent->left){
                    root->next = parent->right;
                }else if(root == parent->right){
                    if(parent->next != NULL)root->next = parent->next->left;
                    else root->next = NULL;
                }
            }
            connect(root->left, root);
            connect(root->right, root);
        }
    };