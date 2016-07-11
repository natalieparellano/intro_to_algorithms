**Problem:** write an `O(n)`-time nonrecursive procedure that, given an `n`-node binary tree prints out the key of each node. Use no more than constant extra space outside the tree itself and do not modify the tree, even temporarily, during the procedure.

**Thoughts**

I thought about this problem for 24 hours before looking up the solution. Here is some C code that I found...let's try to understand it step-by-step with the diagram shown.
```
          A
         / \
        B   C
       / \   \
      D   E   F
     / \      |
    H   I     J
       / \
      M   N   
```
```
struct tree_t {
    struct tree_t *left;
    struct tree_t *right;
    struct tree_t *parent;
    int key;
};
typedef struct tree_t tree_t;
```
Define a tree...a tree has a left child, a right child, and a parent. At the beginning of the problem, left is `B`, right is `C`, and parent is `NIL`.

<-- Does this mean that the tree is NOT singly linked? If a tree always knows about it's parent isn't that doubly linked? If this is the case then...I spent a lot of time barking up the wrong tree! (No pun intended...)
```
void store(int);

void print_tree(tree_t *tree) {
    tree_t *prev;
    prev = 0;

    while (tree) {
        if (prev == tree->parent) {
            store(tree->key);
            prev = tree;
            tree = tree->left  ? tree->left :
                   tree->right ? tree->right :
                                 tree->parent;
        } else if (prev == tree->left && tree->right) {
            prev = tree;
            tree = tree->right;
        } else {
            prev = tree;
            tree = tree->parent;
        }
    }
}
```
What I believe this is saying, in effect, is this:

We have two "pointers" - one is called `tree`, and the other `prev`. We start by recording the value of `tree`...then we move `prev` to also point to `tree`.

Now we need to decide where to move `tree`...as long as `tree` has a left child, we'll move `tree` to point to the left child. We'll then move `prev` to follow `tree` so that the two pointers are inching down the left-most side of the tree until we get to `tree` pointing to `H` and `prev` pointing to `D`. Then, `prev` will move to point to `H`, and `tree`, because it doesn't have a left or right child, will move to point to its parent, which is `D`. 

The next time we run through the `while` loop, `prev == tree->parent` will be `false`. `prev == tree->left && tree->right` will be `true`, so we will move `prev` to point to `tree` (`D`), and `tree` will point to `I`. Then we will again inch down the left side of this branch of the tree so that `tree` is pointing to `M` and `prev` is pointing to `I`. 

Then, as before, we will swap `prev` and `tree`, and move `tree` to its right child which is `N`. `prev` moves back up to point to `I`. 

At this point, `prev == tree->parent` is `true`, but `tree` does not have a left or right child. So `tree` will move to point to its parent, which is `I`. `prev` is now pointing at `N`.

The next time we run through the `while` loop, we will hit the `else` condition which instructs us to inch back up the tree. Now `tree` is pointing to `D` and `prev` is pointing to `I`. On the next iteration we will inch up again so that `tree` points to `B` and `prev` points to `D`. We are now in a place where `prev == tree->left && tree->right` is true again, so we will swap `tree` and `prev` and start inching down the next branch. 

If effect, we are conducting a depth-first search, but instead of queuing up nodes to visit later when we branch, we are walking back up the tree until we find those nodes again. We definitely visit each node more than once - but is the runtime still `O(n)` (assuming some constant factor of `n`)? I'm not sure how to demonstrate this...will come back to this one later. 

Here is the rest of the C code:
```
#define MAX_SIZE 10
int keys[MAX_SIZE];
int count = 0;

void reset_storage() {
    count = 0;
}

void store(int key) {
    keys[count++] = key;
}
```