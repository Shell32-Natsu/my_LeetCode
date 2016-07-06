#Reorder List

[Reorder List](https://leetcode.com/problems/reorder-list/ "Reorder List")

将链表的第`n + 1`个节点插入到第`0`个节点后,第`n`个插入到第`1`个节点后,依次类推.我的方法是使用O(n)的辅助空间,先构造一个反向链表,然后再进行插入,代码一次通过,嘿嘿.

C++:

    class Solution {
    public:
        void reorderList(ListNode *head) {
            if(head == NULL)return;
            int list_len = 0;
            ListNode *reverse_head = NULL, *reverse_node = NULL, *reverse_node_prev = NULL, *node = head;
            while(node){
                list_len++;
                reverse_node = new ListNode(node->val);
                reverse_node->next = reverse_node_prev;
                reverse_node_prev = reverse_node;
                node = node->next;
            }
            reverse_head = reverse_node_prev;
            
            node = head;
            reverse_node = reverse_head;
            ListNode *reverse_node_next = NULL, *node_prev = NULL;
            for(int i = 0; i < list_len / 2; i++){
                reverse_node_next = reverse_node->next;
                reverse_node->next = node->next;
                node->next = reverse_node;
                reverse_node = reverse_node_next;
                node_prev = node->next;
                node = node->next->next;
            }
            if(list_len % 2 == 0){
                node_prev->next = NULL;
            }else{
                node->next = NULL;
            }
            
            return;
        }
    };