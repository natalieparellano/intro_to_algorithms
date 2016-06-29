**Problem:** can you implement the dynamic-set operation `INSERT` on a singly linked list in `O(1)` time? How about `DELETE`?

**Thoughts:** if we have a pointer to an element `x` that should appear *before* the element `y` being inserted, then it can be done in `O(1)` time as we simply have to set `y.next = x.next` and `x.next = y`. The same is true for deleting an element - if we want to delete `x.next`, then we simply set `x.next = x.next.next`.

But if we only have a pointer to the element `y` that we want to delete, it would take `O(n)` time to search the linked list to find the element `x` such that `x.next == y`. 