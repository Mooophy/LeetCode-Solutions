### 160. Intersection of Two Linked Lists
* `Linked List`, `Two Pointers`
* O(n), O(1)
* Although two solutions are pasted here, they are doing the same thing. That is, fill the count gap between two lists, then make two pointers move at the same potions.
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
