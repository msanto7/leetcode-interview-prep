# Binary Search Tree (BST)

    - A Binary Search Tree (BST) is a binary tree where each node follows these properties:

        - Left subtree contains only nodes with values less than the node’s value.
        - Right subtree contains only nodes with values greater than the node’s value.
        - Both left and right subtrees must also be BSTs (i.e., recursively satisfy the above conditions)

    - 



# C#

    - 


## When to use

    - BST's are good for problems that involve fast lookups, insertions, deletions, and ordered data
    - searching for an element O(log(n))
    - finding the kth smallest or largest element
    - ordered traversals
    

    Operation	                BST (Balanced)	    BST (Unbalanced)	Hash Table	Sorted Array
    Insert	                    O(log n)	        O(n)	            O(1)	        O(n)
    Search	                    O(log n)	        O(n)	            O(1)	        O(log n)
    Delete	                    O(log n)	        O(n)	            O(1)	        O(n)
    Sorted Order Retrieval	    O(n)	            O(n)	            O(n log n)  	O(n)





