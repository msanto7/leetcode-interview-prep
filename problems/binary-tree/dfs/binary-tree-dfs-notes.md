# Binary Tree - Depth-First Search 

    - binary tree
        - each node can have a maximum of 2 children (0, 1, or 2 children)
        - left and right pointers for each node

    - so this is a tree traversal techinque
    - commonly used for pathfinding, tree manipulation, backtracking, and AI decision making
    
    - Preorder  -   (Root --> Left --> Right)
    - InOrder   -   (Left --> Root --> Right)
    - PostOrder -   (Left --> Right --> Root)

    - there are both recursive and iterative implementations that have there ups and downs

        Recursive Solution
            - clean and easy to read code
            - uses the call stack to handle the recursive calls without us having to manually manage them

        Iterative Solution
            - can be used to avoid stack overflow from recursive calls on deep trees

# C#


## When to use

    - can be used to find a path...but not necessarily the shortest path
    - 
