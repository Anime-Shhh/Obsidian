Given a partially filled Sudoku board (A 9x9 matrix with some numbers filled in). All of the given nums between 1 and 9
**Goal:**
* Each row contaions 1-9 exactly once
* Same for column
* each 3x3 mini matrix contains exactly 1-9 exactly once


code
```python
def solve_sudoku(board):
	cell = find_empty_cell(board)
	if not cell:
		return True
	(row,col) = cell
	for num in range(1,10):
	if is_valid(board, row, col, num):
		board[row][col] = num
		if solve_sudoku(board:
			return true
		board[row][col] = 0
	return False
```