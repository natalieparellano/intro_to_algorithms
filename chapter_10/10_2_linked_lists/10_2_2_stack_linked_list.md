**Problem:** implement a stack using a singly linked list `L`. The operations `PUSH` and `POP` should still take `O(1)` time. 

**Thoughts:** if we consider that elements are pushed onto the head of the list, then `PUSH` is easy to implement in `O(1)` time since we have a pointer to `L.head`. But to `POP` in `O(1)` time seems impossible...even if we maintained a pointer to the next-to-the-last element in the list, to update that pointer after popping an element would require `O(n)` time to update the pointer to point to its predecessor. 

I'll admit to searching the internet for help with this one. The solution surprised me in its simplicity - reverse the direction of the elements! We can maintain a pointer to the last element in the list...then pushing is still `O(1)` time, we'd just need to remember to update the pointer after we add an element. Add popping becomes simple too, because we already have a pointer to `L.head` which would get updated when an element is removed. 

Having two pointers is part of the solution here, and seems like a useful tool for other problems. But the key here was the additional bit of reversing the direction of the list. 
