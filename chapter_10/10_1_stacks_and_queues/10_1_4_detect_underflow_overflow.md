**Problem:** rewrite `ENQUEUE` and `DEQUEUE` to detect underflow and overflow of a queue. 

**Thoughts:**

  * Modular arithmetic is a clean way to set the new values of head and tail without conditionals 

```
ENQUEUE( Q, x )
if (( Q.head - Q.tail ) % Q.length ) == 1 // Queue is full
  error "overflow"
else 
  Q[Q.tail] = x
  Q.tail = ( Q.tail + 1 ) % Q.length
```

```
DEQUEUE( Q )
if Q.head == Q.tail // Queue is empty
  error "underflow"
else
  x = Q[Q.head]
  Q.head = ( Q.head + 1 ) % Q.length
  return x 
```