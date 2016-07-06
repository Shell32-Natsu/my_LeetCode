#Remove Duplicates from Sorted List

[Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/ "Remove Duplicates from Sorted List")

删除链表重复项，没有难度。

C++:

    class Solution {
    public:
        ListNode *deleteDuplicates(ListNode *head) {
            ListNode *node = head, *true_next;
            
            while(node){
                while(node->next != NULL && node->next->val == node->val){
                    node->next = node->next->next;
                }
                node = node->next;
            }
            
            return head;
        }
    };