# LeetCode -- 36. Valid Sudoku (Medium)

    - validating a 9x9 sudoku board
    - only validate filled cells
    - Rules
        - each row must contain 1-9 no repitiion
        - each column must contain 1-9 no repition
        - each 3x3 sub box must contain 1-9 no repitition
    - so could use a hashset for keeping track of the rows and reset each row
    - same for the columns
    - return false - if any repition
    - and then need to figure out how to section out and loop through the 3x3s
    
    - so nested for loops comes to mind first just for the rows and columns
    - so I will run with that and then address the 3x3s
    - the rows and columns comes easy
    - and then addressing the box is pretty simple once you realize you can divide the row/col index by 3 and that translates to a x, y that corresponds to which box you are in
    - so we can do this in O(n^2)


# Primitive Solution - (Time: O(n^2), Space: O(n))

    -

    public bool IsValidSudoku(char[][] board) {
        HashSet<char> hRow = new HashSet<char>();
        HashSet<char> hCol = new HashSet<char>();
        HashSet<(int, int, char)> hBox = new HashSet<(int, int, char)>();
        
        int rows = board.Length;
        int cols = board[0].Length;

        for (int row = 0; row < rows; row++)
        {
            for (int col = 0; col < cols; col++)
            {
                if ((hRow.Contains(board[row][col]) && board[row][col] != '.') ||
                        (hCol.Contains(board[col][row]) && board[col][row] != '.') ||
                        (hBox.Contains((row / 3, col / 3, board[row][col])) && board[row][col] != '.'))
                {
                    return false;
                }
                else
                {
                    hRow.Add(board[row][col]);
                    hCol.Add(board[col][row]);
                    hBox.Add((row / 3, col / 3, board[row][col]));
                }
            }
            hRow.Clear();
            hCol.Clear();
        }

        return true;
    }





