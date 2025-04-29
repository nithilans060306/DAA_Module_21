# EX 3C Sudoku Solver
## DATE: 12/04/2025
## AIM: To write a python program to find the solution of sudoku puzzle using Backtracking.

## Algorithm:

1. **Input**
   - Start with a 9×9 Sudoku board, where empty cells are marked with `0`.

2. **Backtracking Function (`solve`)**
   - Loop through each cell in the board:
     - If the cell is `0` (empty):
       - Try placing digits `1` to `9`:
         - For each digit, check if it's **valid** to place using `isPossible` function:
           - Check if the digit is not already in the current row.
           - Check if the digit is not already in the current column.
           - Check if the digit is not already in the 3×3 sub-grid.
         - If valid:
           - Place the digit temporarily.
           - Recurse to continue solving the rest of the board.
           - If recursion doesn't lead to solution, backtrack by resetting the cell to `0`.
       - After trying all digits, if none work, return (backtrack).
   - If no empty cells are left, print the board (solution found).

3. **Helper Function (`isPossible`)**
   - Checks whether placing a digit at `board[row][col]` is valid based on:
     - Current row.
     - Current column.
     - 3×3 sub-grid corresponding to the cell.

4. **Print Function (`printBoard`)**
   - Prints the solved Sudoku board row by row.

5. **Main**
   - Call `solve()` to begin solving the board using backtracking.
   

## Program:
```python
/*
Program to implement to to find the solution of sudoku puzzle using Backtracking.
Developed by: Nithilan S
Register Number: 212223240108
*/
board = [
    [0, 0, 0, 8, 0, 0, 4, 0, 3],
    [2, 0, 0, 0, 0, 4, 8, 9, 0],
    [0, 9, 0, 0, 0, 0, 0, 0, 2],
    [0, 0, 0, 0, 2, 9, 0, 1, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 7, 0, 6, 5, 0, 0, 0, 0],
    [9, 0, 0, 0, 0, 0, 0, 8, 0],
    [0, 6, 2, 7, 0, 0, 0, 0, 1],
    [4, 0, 3, 0, 0, 6, 0, 0, 0]
]

def printBoard(board):
    for i in range(0, 9):
        for j in range(0, 9):
            print(board[i][j], end=" ")
        print()

def isPossible(board, row, col, val):
    for j in range(0, 9):
        if board[row][j] == val:
            return False

    for i in range(0, 9):
        if board[i][col] == val:
            return False

    startRow = (row // 3) * 3
    startCol = (col // 3) * 3
    for i in range(0, 3):
        for j in range(0, 3):
            if board[startRow+i][startCol+j] == val:
                return False
    return True

def solve():
    #####################  Add your code here #########################
    for i in range(9):
        for j in range(9):
            if board[i][j] == 0:
                for val in range(1, 10):
                    if isPossible(board, i, j, val):
                        board[i][j] = val
                        solve()
                        board[i][j] = 0
                return
    printBoard(board)
solve()
```

## Output:
![image](https://github.com/user-attachments/assets/9b76a8e1-92b5-4cde-9618-d82fd40d8c4a)



## Result:
The Sudoku solver program executed successfully and found the solution for the given puzzle.
