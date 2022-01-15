# Basic Data Structures
## Stack
- `first in, last out` property
- an item can be inserted and removed from a stack
- but an item can only be removed from the stack after all the items added after it are removed first
- supports three operations
  1. Insert (or "Push"): Putting an item into the stack
  2. Peek: Look at the top item of the stack (the last inserted item that's not removed)
  3. Remove (or "Pop"): Remove the top item of the stack
- Usefulness:
  - one of the most fundamental concepts of computer programming
    - recursion: utilizes a stack under the hood
      - As such, Depth-First Search uses a stack, either directly or through the use of recursion
### Implementation
- using an (statically-sized) array and a pointer pointing to the top of the stack (usually the next unused space)
- When inserting an item, we set the value at the pointer to the item and increment the pointer by 1
- When removing an item, we decrease the pointer by 1
- no need to reset the item at the pointer because it isn't accessible by the stack
  - it will be overwritten when more items are inserted
    - might still want to reset it for languages with garbage collectors to prevent memory leaks
### Caution
- In a real world scenario, need to be careful when doing an operation on a stack
  - Removing an item from a stack with no items will cause an `underflow` error
  - If we have a static sized array as a stack and we try to insert an item into the stack while it's full
    - it will cause an `overflow`
- Underflow errors can be prevented by checking if the stack is empty before removing an item from the stack
  - as programs almost never want to pop from an empty stack
  - If a program does want that, that program probably wants to do something different if the stack is empty
  - `Overflow` errors are a bit tricky, as programs sometimes would like to add more items to the stack
- for modern programming languages, there is usually a dynamically sized array data structure and can be used as a stack
  - Insertion and deletion from the list has a time complexity of O(1) (on average), just like a stack
  - Since memories are dynamically assigned to the list, don't have to worry about overflowing
    - because if it reaches a max size, the system will just allocate more memory for them
  - e.g.: python
    ```python
    # Initializes the stack
    stack = []
    # Pushing 5 into the stack
    stack.append(5)
    # Look at the top item of the stack and print it
    print(stack[-1])
    # Removing the top item from the stack
    stack.pop()
    ```
