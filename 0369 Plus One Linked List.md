### 369. Plus One Linked List
* `Linked List`
* O(n), O(1) (ignored overhead for recursion)
* LI: 
```
Linked list nodes amoung current head to tail have been processed for +1 calculation
```
* C++
```cpp
class Solution {
public:
    ListNode* plusOne(ListNode* head) {
        int carry = 0;
        plusOne(head, carry);
        return carry ? new ListNode{ carry, head } : head;     
    }
    
    void plusOne(ListNode* head, int& carry){
        if(head->next){
            plusOne(head->next, carry);    
        }
        
        int sum = head->val + carry + (head->next ? 0 : 1);
        carry = sum / 10;
        head->val = sum % 10;
    }
};
```
