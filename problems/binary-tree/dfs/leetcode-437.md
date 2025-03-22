# LeetCode -- 437. Path Sum III (Medium)

    - input is a root node and a target sum integer
    - need to return an integer number of the count of paths here the sum of the values is equal to the target
    - so we will at least have to visit each node once that is for sure
    - also the path can only travel from parent nodes to children ("downwards")
    - meaning we can't be going up and down levels to get the sum
    - the values can be negative - which would be a good thing to explicitly ask in a interview
    - think the concept with dfs is pretty simple here...so going to try to implement a recursive solution

    - meh i already see a flaw in my logic
    - if I am checking along a path that we have gone above the target sum...and lets say i am 3 nodes down
    - I can't reset and start at sum 0 from the current node...I would have to do so from node 2
    - so I need to be able to look back far enough somehow

    - so I ran into a problem with my solution
    - in one way i solved the look back problem by recalling my recursive function at each node
    - but now any good nodes below are potentially getting double triple...exponentially counted
    - so took a look at the editorial to get my bearings 
    - they are using a hashmap almost like a stack as they process through the tree



# Recursive Solution - (Time: O(n), Space: O(n))