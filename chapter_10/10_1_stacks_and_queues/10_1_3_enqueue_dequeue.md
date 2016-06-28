**Problem:** illustrate the result of each operation in the sequence `ENQUEUE( Q, 4 )`, `ENQUEUE( Q, 1 )`, `ENQUEUE( Q, 3 )`, `DEQUEUE( Q )`, `ENQUEUE( Q, 8 )`, and `DEQUEUE( Q )` on an initially empty queue `Q` stored in array `Q[1..6]`. 

**Thoughts:** A queue is unlike a stack in that an array of size 6 can only hold 5 elements...we always hold one slot empty for the `tail`. I'm curious as to why this should be the case...I believe it is because this allows us to declare the queue "empty" if `Q.tail == Q.head`. If we allowed the array to fill up completely with 6 elements, then when `Q.tail == Q.head` we don't know if the element in that index is really in the queue, or if it has been de-referenced.

1. Initialize an array of integers `Q` with size 6 
1. Initialize two integer variables, `head` and `tail` to keep track of the indexes of `Q.head` and `Q.tail` ...they will both be zero to start 

...the rest of the algorithm needs to be updated to detect underflow and overflow of a queue, which is the next exercise.

The final result of this operation would be `[4, 1, 3, 8, X, X]` with `head == 2`, pointing to the element `3`, and `tail == 4`, pointing to `X`, which is some random value. Whatever `tail` is pointing to is assumed to be an empty value. 
