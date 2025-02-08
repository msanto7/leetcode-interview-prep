## String Builder
    - dynamic object
    - avoids the immutable properties of normal strings
    - easily expands
    - faster than string for frequent modifications
    - modifies the same object, reducing memory overhead
    
    C# Specific
        - System.Text


# Big(O)

    - for strings...altering them happens in O(n^2) time complexity
        - new string and associated pointer is createed for each modification
    - for string builder...altering happens in O(1) constant time
    - convertnig string builder back to string is O(n) time 

# Implementation


# Helpful Refresher Links

    https://www.geeksforgeeks.org/c-sharp-string-vs-stringbuilder/?ref=lbp



