# LeetCode -- 22. Generate Parentheses (Medium)

    - input is a single integer
    - mean't to represent the amount of pairs of parentheses
    - need to generate all combinations of well-formed parentheses
    - and return a list of strings of those 
    - so I guess there is alwas the option of putting all the open closed pairs just next to each other
    - then there are various nesting options as long as the order of closure remains in tact
    
    - so this is a stack question...so there has to be some way of using a stack to assist
    - but nothing is coming to mind right now
    - definitely wonder if there is a particular correlation between the number of parentheses and the number of valid options
    - but i don't currently see that pattern
    - also not really sure how this could be done in any less than n^2
    - i will say all string lengths need to be n * 2
    - and we can always print n pairs...then n opening followed by n closing parentheses

    - besides the first slot which has to be an open paren...all others can be open or close (except the last) depending on the prior paren
    - 



# Primtive Solution - (Time: O(n), Space: O(n))

    - 








