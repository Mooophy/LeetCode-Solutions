### 2. Add Two Numbers
* `Linked List`
* O(n), O(1)
* C++
```cpp
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* a, ListNode* b) {
        ListNode* head = nullptr, *tail = nullptr;
        
        for(int carry = 0; a || b || carry; a = a ? a->next : nullptr, b = b ? b->next : nullptr){
            int sum = carry + (a ? a->val : 0) + (b ? b->val : 0);
            carry   = sum / 10;
            
            if(!head){
                head = tail       = new ListNode(sum % 10);
            }else{
                tail = tail->next = new ListNode(sum % 10);
            }
        }
        
        return head;
    }
};
```
* C#
```csharp
public class Solution {
    public ListNode AddTwoNumbers(ListNode a, ListNode b) {
        ListNode head = null, tail = null;
        
        for(int carry = 0; a != null || b != null || carry != 0; ){
            int froma = a != null ? a.val : 0;
            int fromb = b != null ? b.val : 0;
            int sum = carry + froma + fromb;
            carry = sum / 10;
            var created = new ListNode(sum % 10);
            
            if(head == null){
                head = tail = created;
            }else{
                tail = tail.next = created;
            }
            
            a = a != null ? a.next : null;
            b = b != null ? b.next : null;
        }
        
        return head;
    }
}
```
