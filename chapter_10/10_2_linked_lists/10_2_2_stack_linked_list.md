**Problem:** implement a stack using a singly linked list `L`. The operations `PUSH` and `POP` should still take `O(1)` time. 

**Thoughts:** this is very easy to implement - to push an element `x` we just need `x.next = L.head` and `L.head = x`. To pop an element `x` we just need `L.head = x.next`. Both operations take `O(1)` time. 