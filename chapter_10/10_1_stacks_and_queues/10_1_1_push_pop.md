**Problem:** illustrate the result of each operation in the sequence `PUSH( S, 4 )`, `PUSH( S, 1 )`, `PUSH( S, 3 )`, `POP( S )`, `PUSH( S, 8 )`, and `POP( S )` on an initially empty stack `S` stored in array `S[1..6]`. 

**Thoughts:** it would be nice to try to do this in C. I am thinking something like this:

1. Initialize an array of integers `S` with size 6 
1. Initialize an integer variable `top` to keep track of `S.top` (to hold the index of the top element, if it exists) 
1. To illustrate `PUSH( S, 4 )`, set `top = top+1`, then `S[top] = 4`
  * First check if the stack is full (does `top` equal the length of `S` minus one?)
  * My natural inclination is to do `S[top+1] = 4`, then `top = top+1` ...I don't think it makes any practical difference, but for other data structures the order might be important 
4. To illustrate `POP( S )`, move the pointer to the left:
  * First check if the stack is empty (is `top` pointing to anything?)
  * `top = top-1`
  * `S[top+1]` is the element that was popped off the stack 

Thus we end up with `[4, 1, 8, X, X, X]` in the stack, with `top == 1`, pointing to the element `1`. `X` represents values in the array that are present when the memory is allocated - they could be anything, when I tried the numbers were `0` or random. 

**Further Work**

I tried to get a "static" version of this going in C, so that it would print the values in the array at each step along with the value of `top`. It does work, but it is a little bit ugly - since I don't yet know how to declare functions and use them elsewhere, I couldn't abstract away repetitive work like printing the array. It might be better to complete a basic primer before going further. 

Eventually, it would be nice to make the program interactive so that, given a starting array, we can ask the user to input directions via the command line and print the changes or return an error if the action would cause the stack to overflow or underflow. 
