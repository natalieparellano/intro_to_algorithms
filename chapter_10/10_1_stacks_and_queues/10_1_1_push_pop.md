**Problem:** illustrate the result of each operation in the sequence `PUSH( S, 4 )`, `PUSH( S, 1 )`, `PUSH( S, 3 )`, `POP( S )`, `PUSH( S, 8 )`, and `POP( S )` on an initially empty stack `S` stored in array `S[1..6]`. 

**Thoughts:** it would be nice to try to do this in C. I am thinking something like this:

1. Initialize an array of integers `S` with size 6 
1. Initialize an integer variable `top` to keep track of S.top (to hold the index of the top element, if it exists) 
1. To illustrate `PUSH( S, 4 )`, set `top = top+1`, then `S[top] = 4`
  * First check if the stack is full (does `top` equal the length of `S` minus one?)
  * My natural inclination is to do `S[top+1] = 4`, then `top = top+1` ...I don't think it makes any practical difference, but for other data structures the order might be important 
4. To illustrate `POP( S )`, move the pointer to the left:
  * First check if the stack is empty (is `top` pointing to anything?)
  * `top = top-1`
  * `S[top+1]` is the element that was popped off the stack 

Thus we end up with `[4, 1, 8]` in the stack, with `top == 1`, pointing to the element `1`. 

**Further Work**

This can all be done "statically" at first...maybe printing the values in the array and the value of `top` at each step. 

Eventually, it would be nice to abstract this into functions so that, given a starting array, we can ask the user to input directions via the command line and print the changes or return an error if the action would cause an overflow or underflow. 
