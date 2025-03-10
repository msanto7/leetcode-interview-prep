# LeetCode -- 1448. Count Good Nodes in Binary Tree (Medium)

    - we are given the root node of a binary tree
    - we are returning a count of what is considered a "good" node
    - a good node is defined as one where you can make it to the node from the root without encountering a node value greater than the destination node value

    - so basically at each node...if the path there has a value greater than it...it is not counted as good
    - I almost feel like using a stack and traversing the tree while pushing the values on the stack helps keep track of the values inbeteen X and the root
    - I think I am going to try to traverse the tree like normal recursive DFS
    - so the idea is that whatever node i am at...if it is less than the root or an node inbetween...then it is not a good node
    - 


# Primitive Solution - (Time: O(n), Space: O(n))






