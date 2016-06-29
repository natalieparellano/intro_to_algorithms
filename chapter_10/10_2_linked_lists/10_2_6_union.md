**Problem:** the dynamic-set operation `UNION` takes two disjoint sets `S1` and `S2` as input, and it returns a set `S` consisting of all the elements of `S1` and `S2`. The sets `S1` and `S2` are usually destroyed by the operation. Show how to support `UNION` in `O(1)` time using a suitable list data structure. 

**Thoughts**

  * If `S1` and `S2` are singly-linked lists, we can join them together in `O(1)` time if we have a pointer to `S1.head`, `S2.head`, AND `S1.tail`.
  * If `S1` and `S2` are circular doubly-linked lists, we can join them together in `O(1)` time with only two pointers (to the heads), but it is a bit more complicated...I sought a few hints on this one but mostly forced myself to figure it out on my own. 

  Here is the first thing that I tried, which does not work...

  Imagine this setup:

  `S1` equal to A -> B -> C -> A (doubly linked)
  `S2` equal to D -> E -> F -> D (doubly linked)

  I tried first to join the lists like so: A -> B -> C -> D -> E -> F -> A (doubly linked)

  ```
  A.prev.next = D
  D.prev.next = A
  A.prev = D.prev
  D.prev = ??? // We no longer have the old reference to A.prev
  ```

  I struggled with this for awhile. I drew multiple diagrams that became a mess of unintelligible squiggly lines. It helped to think about the problem in terms of singly-linked lists, which made for clearer pictures. 

  In the attempted solution above, there is information being ignored - the value of `A.next` and `D.next`. Here is what ended up working:

  ```
  A.prev.next = D.next
  D.next.prev = A.prev
  A.prev = D
  D.next = A
  ```

  This leaves us with the following:

  `S` equal to A -> B -> C -> E -> F -> D -> A (doubly linked)
