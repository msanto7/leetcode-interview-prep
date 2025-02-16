# Hash Map / Set

    - hash maps and hash sets are key-value pair stores used for fast lookup, insertion, and deletion
    - Hash sets are a more specific version that only stores unique unordered values
    - they provide constant time O(1) standard operations
    - the keys are hashed using a has function and the result determines the index in an array
    - 


# C#
    
    - this would be most similar to a dictionary in C#

        Dictionary<int, string> map = new Dictionary<int, string>();

    HashSet
        HashSet<int> s = new HashSet<int>();

## When to use

    - frequency counts
    - mapping relationships
    - caching
    - memoizaiton
        - dynamic programming to store previously computed results

    - Use HashMaps for: Key-value mappings, frequency counts, fast lookups.
    - Use HashSets for: Fast duplicate checking, unique elements, set operations.
    - Time Complexity: Both provide O(1) average time complexity but degrade to O(N) in the worst case due to hash collisions.


    Hash Map vs Hash Set

    Problem Type	                        Use HashMap	    Use HashSet
    Counting occurrences	                ✅	            ❌
    Checking for duplicates	                ✅	            ✅
    Finding first unique element	        ✅	            ❌
    Fast lookups by key	                    ✅	            ❌
    Checking element existence	            ✅	            ✅
    Set operations (union, intersection)	❌	            ✅