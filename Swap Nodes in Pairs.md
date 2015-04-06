#Swap Nodes in Pairs

[Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/ "Swap Nodes in Pairs")

交换链表节点。

C++:

    class Solution {
    public:
        ListNode *swapPairs(ListNode *head) {
            if(head == NULL || head->next == NULL) return head;
            ListNode *first = head, *second = head->next, *prev = NULL;
            first->next = second->next;
            second->next = first;
            head = second;
            prev = first;
            first = first->next;
            while(first){
                second = first->next;
                if(second == NULL)break;
                first->next = second->next;
                second->next = first;
                prev->next = second;
                prev = first;
                first = first->next;
            }
            return head;
        }
    };

时间4ms。

另外，交换数据不交换节点。

C++:

    class Solution {
    public:
        ListNode *swapPairs(ListNode *head) {
            if(head == NULL || head->next == NULL) return head;
            ListNode *first = head, *second = head->next, *prev = NULL;
            while(first){
                if(first->next == NULL)break;
                int t = first->val;
                first->val = first->next->val;
                first->next->val = t;
                first = first->next->next;
            }
            return head;
        }
    };

时间8ms。