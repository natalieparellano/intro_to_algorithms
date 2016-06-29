**Problem:** whereas a stack allows insertions and deletion of elements at only one end, and a queue allows insertion at one end and deletion at the other end, a deque allows insertion and deletion at both ends. Write four O(1)-time procedures to insert elements into and delete elements from both ends of a deque implemented by an array. 

**Thoughts:** for it to be O(1) time, we'd need to have prior knowledge of the location where, for each end of the deque, a new value would be inserted. Therefore it seems to me that we'd need to have four pointers. The interesting, and more challenging question comes when we consider what happens when an element is dequeued from either end of the deque, or if the deque becomes full - where do we wrap around to? I'll come back to this problem in a little bit. 