---
title: 36. Valid Sudoku
date: 2016-07-12 14:18:51
tags: leetcode
---

>Determine if a Sudoku is valid, according to: Sudoku Puzzles - The Rules.

>The Sudoku board could be partially filled, where empty cells are filled with the character '.'.

>![sudoku](http://o7mi4viua.bkt.clouddn.com/image/jpg/Sudoku.png)
>A partially filled sudoku which is valid.


```c++
class Solution {
public:
    bool isValidSudoku(vector<vector<char>>& board) {
       int size = board.size();
       vector<int> row(size,0);
       vector<int> col(size,0);
       vector<int> box(size,0);
       
       for (int r = 0; r < size; r++) {
           for (int c = 0; c < size; c++) {
                if (board[r][c] == '.')
                    continue;
                int mask = 1 << (board[r][c] - '0');
                int boxIndex = 3 * (r / 3) + (c / 3);
                if ((row[r] & mask) || (col[c] & mask) || (box[boxIndex] & mask))
                    return false;
                
                row[r] |= mask;
                col[c] |= mask;
                box[boxIndex] |= mask;
           }
       }
       return true;
    }
};
```
