### 160. Intersection of Two Linked Lists
* `Linked List`, `Two Pointers`
* O(n), O(1)
* Although two solutions presented here, they are doing the same thing. That is, fill the count gap between two lists, then make two pointers move at the same potions.
* C++ (Optimized version)
```cpp
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *a, ListNode *b) {
        auto x = a, y = b;
        for(; x != y; x = x ? x->next : b, y = y ? y->next : a);
        return x;
    }
};
```
* C++ (Easy for understanding version)
```cpp
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *a, ListNode *b) {
        if(!a || !b){
            return nullptr;
        }
        
        int counta = 0, countb = 0;
        auto taila = a; auto tailb = b;
        
        for(; taila->next; taila = taila->next, ++counta);
        for(; tailb->next; tailb = tailb->next, ++countb);
        
        if(taila != tailb){
            return nullptr;
        }
        
        auto sht = counta > countb ? b : a;
        auto lng = counta > countb ? a : b;
        for(auto diff = abs(counta - countb); diff; --diff, lng = lng->next);
        
        for(; sht; sht = sht->next, lng = lng->next){
            if(sht == lng){
                return sht;
            }
        }
        
        return nullptr;
    }
};
```
