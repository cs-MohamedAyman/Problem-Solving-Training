<img align="right" width="80" src="https://github.com/cs-MohamedAyman/Problem-Solving-Training/blob/master/logos/leetcode.jpg">

## LeetCode OJ - Phase 4 Interviews Questions - Hard Problems

### first missing positive:
Problem Link: https://leetcode.com/problems/first-missing-positive

#### - Python Solution
```python
class Solution:
    def firstMissingPositive(self, nums: List[int]) -> int:
        for i in range(len(nums)):
            if nums[i] < 0:
                nums[i] = 0
        for i in range(len(nums)):
            val = abs(nums[i])
            if 1 <= val <= len(nums):
                if nums[val-1] > 0:
                    nums[val-1] *= -1
                elif nums[val-1] == 0:
                    nums[val-1] = -(len(nums)+1)
        for i in range(len(nums)):
            if nums[i] >= 0:
                return i+1
        return len(nums)+1
```
#### - CPP Solution
```cpp
class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        for (int i=0; i<size(nums); i++) {
            if (nums[i] < 0)
                nums[i] = 0;
        }
        for (int i=0; i<size(nums); i++) {
            int val = abs(nums[i]);
            if (1 <= val and val <= size(nums)) {
                if (nums[val-1] > 0)
                    nums[val-1] *= -1;
                else if (nums[val-1] == 0)
                    nums[val-1] = -(size(nums)+1);
            }
        }
        for (int i=0; i<size(nums); i++) {
            if (nums[i] >= 0)
                return i+1;
        }
        return size(nums)+1;
    }
};
```

### sudoku solver:
Problem Link: https://leetcode.com/problems/sudoku-solver

#### - Python Solution
```python
class Solution:
    def solveSudoku(self, grid: List[List[str]]) -> None:
        def check_valid_value(i, j, v):
            for k in range(9):
                if grid[i][k] == v or grid[k][j] == v:
                    return False
            b, e = i//3*3, j//3*3
            for k in range(b, b+3):
                for w in range(e, e+3):
                    if grid[k][w] == v:
                        return False
            return True

        def solve_grid(i, j):
            if j == 9:
                i += 1
                j = 0
            if i == 9:
                return True
            if cpy_grid[i][j] != '.':
                return solve_grid(i, j+1)
            for k in range(1, 10):
                t = chr(k+ord('0'))
                if check_valid_value(i, j, t):
                    grid[i][j] = t
                    cpy_grid[i][j] = t
                    if solve_grid(i, j+1):
                        return True
                    grid[i][j] = '.'
                    cpy_grid[i][j] = '.'
            return False

        cpy_grid = [[i for i in j] for j in grid]
        solve_grid(0, 0)
```
#### - CPP Solution
```cpp
class Solution {
    bool check_valid_value(vector<vector<char>> &grid, int i, int j, int v) {
        for (int k = 0; k < 9; k++)
            if (grid[i][k] == v or grid[k][j] == v)
                return false;
        int b = i/3*3, e = j/3*3;
        for (int k = b; k < b+3; k++)
            for (int w = e; w < e+3; w++)
                if (grid[k][w] == v)
                    return false;
        return true;
    }
    bool solve_grid(vector<vector<char>> &cpy_grid, vector<vector<char>> &grid, int i, int j) {
        if (j == 9) {
            i += 1;
            j = 0;
        }
        if (i == 9)
            return true;
        if (cpy_grid[i][j] != '.')
            return solve_grid(cpy_grid, grid, i, j+1);
        for (int k = 1; k < 10; k++) {
            char t = k+'0';
            if (check_valid_value(grid, i, j, t)) {
                grid[i][j] = t;
                cpy_grid[i][j] = t;
                if (solve_grid(cpy_grid, grid, i, j+1))
                    return true;
            }
            grid[i][j] = '.';
            cpy_grid[i][j] = '.';
        }
        return false;
    }
public:
    void solveSudoku(vector<vector<char>> &grid) {
        vector<vector<char>> cpy_grid(grid);
        solve_grid(cpy_grid, grid, 0, 0);
    }
};
```

### n queens:
Problem Link: https://leetcode.com/problems/n-queens

#### - Python Solution
```python
class Solution:
    def solveNQueens(self, n: int) -> List[List[str]]:
        def backtrack(r):
            if r == n:
                curr_board = ["".join(row) for row in board]
                res.append(curr_board)
                return
            for c in range(n):
                if c in col or (r+c) in pos_diag or (r-c) in neg_diag:
                    continue
                col.add(c)
                pos_diag.add(r+c)
                neg_diag.add(r-c)
                board[r][c] = 'Q'
                backtrack(r+1)
                col.remove(c)
                pos_diag.remove(r+c)
                neg_diag.remove(r-c)
                board[r][c] = '.'

        col = set()
        pos_diag = set()
        neg_diag = set()
        res = []
        board = [['.' for j in range(n)] for i in range(n)]
        backtrack(0)
        return res
```
#### - CPP Solution
```cpp
class Solution {
    set<int> col;
    set<int> pos_diag;
    set<int> neg_diag;

    void backtrack(int r, int n, vector<string> &board, vector<vector<string>> &res) {
        if (r == n) {
            vector<string> curr_board(board);
            res.push_back(curr_board);
            return;
        }
        for (int c=0; c<n; c++) {
            if (col.find(c) != col.end() or
                pos_diag.find(r+c) != pos_diag.end() or
                neg_diag.find(r-c) != neg_diag.end())
                continue;
            col.insert(c);
            pos_diag.insert(r+c);
            neg_diag.insert(r-c);
            board[r][c] = 'Q';
            backtrack(r+1, n, board, res);
            col.erase(col.find(c));
            pos_diag.erase(pos_diag.find(r+c));
            neg_diag.erase(neg_diag.find(r-c));
            board[r][c] = '.';
        }
    }
public:
    vector<vector<string>> solveNQueens(int n) {
        vector<vector<string>> res;
        vector<string> board(n, string(n, '.'));
        backtrack(0, n, board, res);
        return res;
    }
};
```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```
