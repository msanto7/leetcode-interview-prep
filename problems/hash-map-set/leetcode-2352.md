# LeetCode -- 2352. Equal Row and Column Pairs (Medium)

    - n x n matrix grid
    - returning a count of the pairs 
    - pairs must have equal row and column (same elements in same order)

    - so we could obviously compare the rows and columns using brute force loops
    - but I am guessing we could use a hashmap and count as we find duplicates...or just return the highest freq count or something
    - we are still going to have to traverse each row/column though

    - alright so I have filled a hashmap of string conveted rows...and frequency counts
    - now I need to compare to columns 

    - 1 clarifying question i would have is can a row be repeated...because that might change some of my comparison logic



# Optimized Solution - (Time: O(n^2), Space: O(n^2))

    - alright so I got to this solution without any help
    - it seems a bit hacky...is O(n^2) time...but builds a hashmap of strings of rows and columns
    - then compares and counts at the end for matches

    ** looks like there is a Trie solution to this problem as well but I am going to hold off until i get to that section to learn that structure


    public int EqualPairs(int[][] grid) {
        Dictionary<string, int> rows = new Dictionary<string, int>();
        Dictionary<string, int> cols = new Dictionary<string, int>();
        StringBuilder sbR = new StringBuilder();
        StringBuilder sbC = new StringBuilder();

        for (int i = 0; i < grid.Length; i++) // rows
        {
            for (int j = 0; j < grid.Length; j++) // col
            {
                // row
                sbR.Append(grid[i][j].ToString() + ",");
                // col
                sbC.Append(grid[j][i].ToString() + ",");
            }

            //rows.Add(sb.ToString(), 1);
            rows[sbR.ToString()] = rows.GetValueOrDefault(sbR.ToString()) + 1;
            sbR.Clear();

            cols[sbC.ToString()] = cols.GetValueOrDefault(sbC.ToString()) + 1;
            sbC.Clear();
        }

        int count = 0;

        // compare the keys between the 2 dictionaries
        foreach (var x in rows.Keys)
        {
            if (cols.ContainsKey(x))
            {
                count = count + (rows[x] * cols[x]);
            }
        }

        return count;
    }

