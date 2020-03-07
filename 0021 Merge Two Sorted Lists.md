### 21. Merge Two Sorted Lists
* `Linked List`, `Two Pointers`
* O(n), O(1)
* C++
```cpp
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* a, ListNode* b) {
        ListNode* head = nullptr, * tail = nullptr;
        
        while(a && b){
            auto& curr = a->val < b->val ? a : b;
            
            if(head){
                tail = tail->next = curr;
            }else{
                head = tail = curr;
            }
            
            auto temp = curr;
            curr = curr->next;
            temp->next = nullptr;
        }
        
        (head ? tail->next : head) = a ? a : b; // link the rest     
        
        return head;
    }
};
```
