### 369. Plus One Linked List
* `Linked List`
* O(n), O(1) (ignored overhead caused by recursion)
* LI
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
