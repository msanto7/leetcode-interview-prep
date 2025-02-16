# Stack

    - LIFO - last in first out
    - push, pop, peek
    - useful for problems where you need to keep track of previous states or elemints in a specific order (think call stack)

    - Look for LIFO structure: Whenever the problem requires you to process elements in reverse order, 
        or maintain states that need to be "undone" or "popped," stacks are a good fit.
    - Track previous states: If you need to remember elements in the past to compare with the current one, 
        use a stack to push and pop the states.
    - Be mindful of performance: In many problems, the stack's Push() and Pop() operations are efficient (O(1)). 
        But watch out for issues like repeated dictionary lookups.
    - Avoid nested loops where possible: Stacks allow you to solve many problems iteratively, 
        preventing you from using deep recursion or nested loops.

# C#

    - Stack<T> class


## When to use

    - balanced parentheses/brackets
    - depth-first-search (DFS) and Backtracking problems
    - tree traversal and graph searches can be implemented with stacks


    Problem Type	                                Stack Use Case
    - Balanced Parentheses/Brackets	                - Push opening, pop closing brackets
    - DFS and Backtracking	                        - Push/Pop nodes or states for traversal
    - Next Greater Element	                        - Track previous elements while finding next greater
    - Sliding Window/Maximum Sliding Window	        - Keep track of window elements
    - Subsequence Matching	                        - Track order of characters