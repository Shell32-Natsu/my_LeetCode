#Merge Two Sorted Lists

[Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/ "Merge Two Sorted Lists")

简单的链表操作。

C++:

    class Solution {
    public:
        ListNode *mergeTwoLists(ListNode *l1, ListNode *l2) {
            if(l1 == NULL && l2 == NULL)return NULL;
            if(l1 == NULL)return l2;
            if(l2 == NULL)return l1;
            ListNode *head, *node;
            if(l1->val < l2->val){
                head = l1;
                l1 = l1->next;
            }else{
                head = l2;
                l2 = l2->next;
            }
            node = head;
            while(l1 && l2){
                if(l1->val < l2->val){
                    node->next = l1;
                    l1 = l1->next;
                }else{
                    node->next = l2;
                    l2 = l2->next;
                }
                node = node->next;
            }
            if(l1 == NULL){
                node->next = l2;
            }else if(l2 == NULL){
                node->next = l1;
            }
            
            return head;
        }
    };