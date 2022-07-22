<img align="right" width="80" src="https://github.com/cs-MohamedAyman/Problem-Solving-Training/blob/master/online-judges-logos/leetcode.jpg">

## LeetCode OJ - Phase 4 Interviews Questions - Medium Problems I

### product of array except self:
https://leetcode.com/problems/product-of-array-except-self

#### - Python Solution
```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        res = [1] * len(nums)
        for i in range(len(nums)-1):
            res[i+1] *= res[i] * nums[i]
        prod = 1
        for i in range(len(nums)-1, -1, -1):
            res[i] *= prod
            prod *= nums[i]
        return res
```
#### - CPP Solution
```cpp
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        vector<int> res(nums.size(), 1);
        for (int i=0; i<nums.size()-1; i++)
            res[i+1] *= res[i] * nums[i];
        int prod = 1;
        for (int i=nums.size()-1; i>-1; i--) {
            res[i] *= prod;
            prod *= nums[i];
        }
        return res;
    }
};
```

### find the duplicate number:
https://leetcode.com/problems/find-the-duplicate-number

#### - Python Solution
```python
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        p1, p2 = nums[0], nums[0]
        for i in range(len(nums)):
            p1 = nums[p1]
            p2 = nums[nums[p2]]
            if p1 == p2:
                break
        p2 = nums[0]
        for i in range(len(nums)):
            if p1 == p2:
                break
            p1 = nums[p1]
            p2 = nums[p2]
        return p1
```
#### - CPP Solution
```cpp
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        int p1 = nums[0], p2 = nums[0];
        for (int i=0; i<nums.size(); i++) {
            p1 = nums[p1];
            p2 = nums[nums[p2]];
            if (p1 == p2)
                break;
        }
        p2 = nums[0];
        for (int i=0; i<nums.size(); i++) {
            if (p1 == p2)
                break;
            p1 = nums[p1];
            p2 = nums[p2];
        }
        return p1;
    }
};
```

### find all duplicates in an array:
https://leetcode.com/problems/find-all-duplicates-in-an-array

#### - Python Solution
```python
class Solution:
    def findDuplicates(self, nums: List[int]) -> List[int]:
        res = []
        for i in range(len(nums)):
            if nums[abs(nums[i])-1] > 0:
                nums[abs(nums[i])-1] *= -1
            else:
                res.append(abs(nums[i]))
        return res
```
#### - CPP Solution
```cpp
class Solution {
public:
    vector<int> findDuplicates(vector<int>& nums) {
        vector<int> res;
        for (int i=0; i<nums.size(); i++) {
            if (nums[abs(nums[i])-1] > 0)
                nums[abs(nums[i])-1] *= -1;
            else
                res.push_back(abs(nums[i]));
        }
        return res;
    }
};
```

### set matrix zeroes:
https://leetcode.com/problems/set-matrix-zeroes

#### - Python Solution
```python
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        n, m = len(matrix), len(matrix[0])
        zero_rows = [0] * n
        zero_cols = [0] * m
        for i in range(n):
            for j in range(m):
                if matrix[i][j] == 0:
                    zero_rows[i] = zero_cols[j] = 1
        for i in range(n):
            for j in range(m):
                if zero_rows[i] or zero_cols[j]:
                    matrix[i][j] = 0
```
#### - CPP Solution
```cpp
class Solution {
public:
    void setZeroes(vector<vector<int>>& matrix) {
        int n = matrix.size(), m = matrix[0].size();
        vector<int> zero_rows(n, 0);
        vector<int> zero_cols(m, 0);
        for (int i=0; i<n; i++) {
            for (int j=0; j<m; j++) {
                if (matrix[i][j] == 0)
                    zero_rows[i] = zero_cols[j] = 1;
            }
        }
        for (int i=0; i<n; i++) {
            for (int j=0; j<m; j++) {
                if (zero_rows[i] or zero_cols[j])
                    matrix[i][j] = 0;
            }
        }
    }
};
```

### spiral matrix:
https://leetcode.com/problems/spiral-matrix

#### - Python Solution
```python
class Solution:
    def spiralOrder(self, matrix: List[List[int]]) -> List[int]:
        d = [(0, 1), (1, 0), (0, -1), (-1, 0)]
        curr_dir, x, y = 0, 0, -1
        n, m = len(matrix), len(matrix[0])
        visited = [[0 for i in range(m)] for j in range(n)]
        res = [0] * (n*m)
        res_idx = 0
        for i in range(n):
            for j in range(m):
                x += d[curr_dir][0]
                y += d[curr_dir][1]
                res[res_idx] = matrix[x][y]
                res_idx += 1
                visited[x][y] = 1
                if not (0 <= x+d[curr_dir][0] < n and 0 <= y+d[curr_dir][1] < m) or \
                   visited[x+d[curr_dir][0]][y+d[curr_dir][1]]:
                    curr_dir = (curr_dir + 1) % 4
        return res
```
#### - CPP Solution
```cpp
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        vector<pair<int, int>> d = {{0, 1}, {1, 0}, {0, -1}, {-1, 0}};
        int curr_dir = 0, x = 0, y = -1;
        int n = matrix.size(), m = matrix[0].size();
        vector<vector<int>> visited(n, vector<int>(m, 0));
        vector<int> res(n*m, 0);
        int res_idx = 0;
        for (int i=0; i<n; i++) {
            for (int j=0; j<m; j++) {
                x += d[curr_dir].first;
                y += d[curr_dir].second;
                res[res_idx] = matrix[x][y];
                res_idx ++;
                visited[x][y] = 1;
                if (not (0 <= x+d[curr_dir].first and x+d[curr_dir].first < n and
                         0 <= y+d[curr_dir].second and y+d[curr_dir].second < m) or
                    visited[x+d[curr_dir].first][y+d[curr_dir].second])
                    curr_dir = (curr_dir + 1) % 4;
            }
        }
        return res;
    }
};
```

### rotate image:
https://leetcode.com/problems/rotate-image

#### - Python Solution
```python
class Solution:
    def rotate(self, matrix: List[List[int]]) -> None:
        n = len(matrix)
        for i in range(n//2):
            for j in range(i, n-i-1):
                k                    = matrix[i][j]
                matrix[i][j]         = matrix[n-j-1][i]
                matrix[n-j-1][i]     = matrix[n-i-1][n-j-1]
                matrix[n-i-1][n-j-1] = matrix[j][n-i-1]
                matrix[j][n-i-1]     = k
```
#### - CPP Solution
```cpp
class Solution {
public:
    void rotate(vector<vector<int>>& matrix) {
        int n = matrix.size();
        for (int i = 0; i < n/2; i++) {
            for (int j = i; j < n-i-1; j++) {
                int k                = matrix[i][j];
                matrix[i][j]         = matrix[n-j-1][i];
                matrix[n-j-1][i]     = matrix[n-i-1][n-j-1];
                matrix[n-i-1][n-j-1] = matrix[j][n-i-1];
                matrix[j][n-i-1]     = k;
            }
        }
    }
};
```

### word search:
https://leetcode.com/problems/word-search

#### - Python Solution
```python
class Solution:
    def exist(self, board: List[List[str]], word: str) -> bool:
        def dfs(x, y, idx):
            if idx == len(word):
                return True
            if not(0 <= x < n and 0 <= y < m) or visited[x][y] or \
               board[x][y] != word[idx]:
                return False
            visited[x][y] = 1
            for i, j in d:
                if dfs(x+i, y+j, idx+1):
                    return True
            visited[x][y] = 0
            return False

        n, m = len(board), len(board[0])
        visited = [[0 for i in range(m)] for j in range(n)]
        d = [(0, 1), (1, 0), (-1, 0), (0, -1)]
        for i in range(n):
            for j in range(m):
                if dfs(i, j, 0):
                    return True
        return False
```
#### - CPP Solution
```cpp
class Solution {
public:
    int n, m;
    vector<vector<int>> visited;
    int dx[4] = {0, 0, 1, -1};
    int dy[4] = {1, -1, 0, 0};
    
    bool dfs(int x, int y, int idx, const vector<vector<char>>& board, const string &word) {
        if (idx == word.size())
            return true;
        if (not(0 <= x < n and 0 <= y < m) or visited[x][y] or
           board[x][y] != word[idx])
            return false;
        visited[x][y] = 1;
        for (int i=0; i<4; i++) {
            if (dfs(x+dx[i], y+dy[i], idx+1, board, word))
                return true;
        }
        visited[x][y] = 0;
        return false;
    }
    bool exist(vector<vector<char>>& board, string word) {
        n = board.size(), m = board[0].size();
        visited.assign(n, vector<int>(m, 0));
        for (int i=0; i<n; i++) {
            for (int j=0; j<m; j++) {
                if (dfs(i, j, 0, board, word))
                    return true;
            }
        }
        return false;
    }
};
```
`TODO` RUN-TIME ERROR

### longest consecutive sequence:
https://leetcode.com/problems/longest-consecutive-sequence

#### - Python Solution
```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        longest_len = 0
        set_nums = set(nums)
        for i in set_nums:
            if i - 1 in set_nums:
                continue
            curr_len = 0
            while i + curr_len in set_nums:
                curr_len += 1
            longest_len = max(longest_len, curr_len)
        return longest_len
```
#### - CPP Solution
```cpp
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        int longest_len = 0;
        set<int> set_nums(nums.begin(), nums.end());
        for (int i : set_nums) {
            if (set_nums.find(i - 1) != set_nums.end())
                continue;
            int curr_len = 0;
            while (set_nums.find(i + curr_len) != set_nums.end())
                curr_len ++;
            longest_len = max(longest_len, curr_len);
        }
        return longest_len;
    }
};
```

### letter case permutation:
https://leetcode.com/problems/letter-case-permutation

#### - Python Solution
```python
class Solution:
    def letterCasePermutation(self, s: str) -> List[str]:
        def generate_permutation(i, curr_s):
            if i == len(s):
                res.add(curr_s)
                return
            generate_permutation(i+1, curr_s+s[i].lower())
            generate_permutation(i+1, curr_s+s[i].upper())
            
        res = set()
        generate_permutation(0, '')
        return list(res)
```
#### - CPP Solution
```cpp
class Solution {
public:
    set<string> res;

    void generate_permutation(int i, string curr_s, const string &s) {
        if (i == s.size()) {
            res.insert(curr_s);
            return;
        }
        generate_permutation(i+1, curr_s+char(tolower(s[i])), s);
        generate_permutation(i+1, curr_s+char(toupper(s[i])), s);
    }
    vector<string> letterCasePermutation(string s) {
        generate_permutation(0, "", s);
        vector<string> ans(res.begin(), res.end());
        return ans;
    }
};
```

### subsets:
https://leetcode.com/problems/subsets

#### - Python Solution
```python
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        n = len(nums)
        res = []
        for i in range(1<<n):
            curr_list = []
            for j in range(n):
                if 1<<j & i:
                    curr_list.append(nums[j])
            res.append(curr_list)
        return res
```
#### - CPP Solution
```cpp
class Solution {
public:
    vector<vector<int>> subsets(vector<int>& nums) {
        int n = nums.size();
        vector<vector<int>> res;
        for (int i=0; i<(1<<n); i++) {
            vector<int> curr_list;
            for (int j=0; j<n; j++)
                if (1<<j & i)
                    curr_list.push_back(nums[j]);
            res.push_back(curr_list);
        }
        return res;
    }
};
```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```
