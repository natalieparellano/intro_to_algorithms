**Problem:** implement a queue by a singly linked list `L`. The operations `ENQUEUE` and `DEQUEUE` should still take `O(1)` time. 

**Thoughts:** To enqueue an element `x` is easy, we just need `x.next = L.head` and `L.head = x` which takes `O(1)` time. But to dequeue an element in `O(1)` time seems impossible...even if we maintained a pointer to the next-to-the-last element in the list, to update that pointer after dequeuing an element would require `O(n)` time to update the pointer to point to its predecessor. 

I'll admit to searching the internet for help with this one. The solution surprised me in its simplicity - reverse the direction of the elements! We can maintain a pointer to the last element in the list...then enqueuing is still `O(1)` time: `L.tail.next = x` and `L.tail = x`. Dequeuing `x` at the front of the list then becomes very simple: `L.head = x.next`.

Having two pointers is part of the solution here, and seems like a useful tool for other problems. But the key here was the additional bit of reversing the direction of the list. 
