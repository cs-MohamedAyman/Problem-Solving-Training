<img align="right" width="80" src="https://github.com/cs-MohamedAyman/Problem-Solving-Training/blob/master/online-judges-logos/leetcode.jpg">

## LeetCode OJ - Phase 4 Interviews Questions - Medium Problems I

### product of array except self:
Problem Link: https://leetcode.com/problems/product-of-array-except-self

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
Problem Link: https://leetcode.com/problems/find-the-duplicate-number

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
Problem Link: https://leetcode.com/problems/find-all-duplicates-in-an-array

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
Problem Link: https://leetcode.com/problems/set-matrix-zeroes

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
Problem Link: https://leetcode.com/problems/spiral-matrix

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
Problem Link: https://leetcode.com/problems/rotate-image

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
Problem Link: https://leetcode.com/problems/word-search

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
public:
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
Problem Link: https://leetcode.com/problems/longest-consecutive-sequence

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
Problem Link: https://leetcode.com/problems/letter-case-permutation

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
    set<string> res;

    void generate_permutation(int i, string curr_s, const string &s) {
        if (i == s.size()) {
            res.insert(curr_s);
            return;
        }
        generate_permutation(i+1, curr_s+char(tolower(s[i])), s);
        generate_permutation(i+1, curr_s+char(toupper(s[i])), s);
    }
public:
    vector<string> letterCasePermutation(string s) {
        generate_permutation(0, "", s);
        vector<string> ans(res.begin(), res.end());
        return ans;
    }
};
```

### subsets:
Problem Link: https://leetcode.com/problems/subsets

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

### subsets ii:
Problem Link: https://leetcode.com/problems/subsets-ii

#### - Python Solution
```python
class Solution:
    def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
        n = len(nums)
        res = set()
        for i in range(1<<n):
            curr_list = []
            for j in range(n):
                if 1<<j & i:
                    curr_list.append(nums[j])
            res.add(tuple(sorted(curr_list)))
        return list(res)
```
#### - CPP Solution
```cpp
class Solution {
public:
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        int n = nums.size();
        set<vector<int>> res;
        for (int i=0; i<(1<<n); i++) {
            vector<int> curr_list;
            for (int j=0; j<n; j++)
                if (1<<j & i)
                    curr_list.push_back(nums[j]);
            sort(curr_list.begin(), curr_list.end());
            res.insert(curr_list);
        }
        vector<vector<int>> ans(res.begin(), res.end());
        return ans;
    }
};
```

### permutations:
Problem Link: https://leetcode.com/problems/permutations

#### - Python Solution
```python
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        def generate_permutation(arr):
            if len(arr) == 0:
                return []
            if len(arr) == 1:
                return [arr]
            res = []
            for i in range(len(arr)):
                m = arr[i]
                for p in generate_permutation(arr[:i] + arr[i+1:]):
                    res.append([m] + p)
            return res

        return generate_permutation(nums)
```
#### - CPP Solution
```cpp
class Solution {
    vector<vector<int>> generate_permutation(vector<int> arr) {
        if (arr.size() == 0)
            return {};
        if (arr.size() == 1)
            return {arr};
        vector<vector<int>> res;
        for (int i=0; i<arr.size(); i++) {
            int m = arr[i];
            vector<int> sub1(arr.begin(), arr.begin()+i);
            vector<int> sub2(arr.begin()+i+1, arr.end());
            vector<int> sub;
            sub.insert(sub.begin(), sub1.begin(), sub1.end());
            sub.insert(sub.end(),   sub2.begin(), sub2.end());
            for (auto p : generate_permutation(sub)) {
                vector<int> temp(p.begin(), p.end());
                temp.insert(temp.begin(), m);
                res.push_back(temp);
            }
        }
        return res;
    }
public:
    vector<vector<int>> permute(vector<int>& nums) {
        return generate_permutation(nums);
    }
};
```

### permutations ii:
Problem Link: https://leetcode.com/problems/permutations-ii

#### - Python Solution
```python
class Solution:
    def permuteUnique(self, nums: List[int]) -> List[List[int]]:
        def generate_permutation(arr):
            if len(arr) == 0:
                return []
            if len(arr) == 1:
                return [arr]
            res = []
            for i in range(len(arr)):
                m = arr[i]
                for p in generate_permutation(arr[:i] + arr[i+1:]):
                    res.append([m] + p)
            return res

        res = list(set(tuple(i) for i in generate_permutation(nums)))
        return res
```
#### - CPP Solution
```cpp
class Solution {
    vector<vector<int>> generate_permutation(vector<int> arr) {
        if (arr.size() == 0)
            return {};
        if (arr.size() == 1)
            return {arr};
        vector<vector<int>> res;
        for (int i=0; i<arr.size(); i++) {
            int m = arr[i];
            vector<int> sub1(arr.begin(), arr.begin()+i);
            vector<int> sub2(arr.begin()+i+1, arr.end());
            vector<int> sub;
            sub.insert(sub.begin(), sub1.begin(), sub1.end());
            sub.insert(sub.end(),   sub2.begin(), sub2.end());
            for (auto p : generate_permutation(sub)) {
                vector<int> temp(p.begin(), p.end());
                temp.insert(temp.begin(), m);
                res.push_back(temp);
            }
        }
        return res;
    }
public:
    vector<vector<int>> permuteUnique(vector<int>& nums) {
        set<vector<int>> res;
        for (auto p : generate_permutation(nums))
            res.insert(p);
        vector<vector<int>> ans(res.begin(), res.end());
        return ans;
    }
};
```

### combinations:
Problem Link: https://leetcode.com/problems/combinations

#### - Python Solution
```python
class Solution:
    def combine(self, n: int, k: int) -> List[List[int]]:
        def generate_combinations(p, arr):
            if len(arr) == k:
                res.append(arr[:])
                return
            for i in range(p, n+1):
                arr.append(i)
                generate_combinations(i+1, arr)
                arr.pop()

        res = []
        generate_combinations(1, [])
        return res
```
#### - CPP Solution
```cpp
class Solution {
    vector<vector<int>> res;

    void generate_combinations(int p, vector<int> arr, int n, int k) {
        if (arr.size() == k) {
            res.push_back(arr);
            return;
        }
        for (int i=p; i<n+1; i++) {
            arr.push_back(i);
            generate_combinations(i+1, arr, n, k);
            arr.pop_back();
        }
    }
public:
    vector<vector<int>> combine(int n, int k) {
        generate_combinations(1, {}, n, k);
        return res;
    }
};
```

### combination sum:
Problem Link: https://leetcode.com/problems/combination-sum

#### - Python Solution
```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        def generate_combinations(i, arr, curr_total):
            if curr_total == target:
                res.append(sorted(arr[:]))
                return
            if i == len(candidates) or curr_total > target:
                return
            arr.append(candidates[i])
            generate_combinations(i, arr, curr_total+candidates[i])
            arr.pop()
            generate_combinations(i+1, arr, curr_total)

        res = []
        generate_combinations(0, [], 0)
        return res
```
#### - CPP Solution
```cpp
class Solution {
    vector<vector<int>> res;

    void generate_combinations(int i, vector<int >arr, int curr_total, vector<int>& candidates, int target) {
        if (curr_total == target) {
            sort(arr.begin(), arr.end());
            res.push_back(arr);
            return;
        }
        if (i == candidates.size() or curr_total > target)
            return;
        arr.push_back(candidates[i]);
        generate_combinations(i, arr, curr_total+candidates[i], candidates, target);
        arr.pop_back();
        generate_combinations(i+1, arr, curr_total, candidates, target);
    }
public:
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        generate_combinations(0, {}, 0, candidates, target);
        return res;
    }
};
```

### combination sum ii:
Problem Link: https://leetcode.com/problems/combination-sum-ii

#### - Python Solution
```python
class Solution:
    def combinationSum2(self, candidates: List[int], target: int) -> List[List[int]]:
        def generate_combinations(i, arr, curr_total):
            if curr_total == target:
                res.append(sorted(arr[:]))
                return
            if curr_total > target:
                return
            prev = -1
            for j in range(i, len(candidates)):
                if candidates[j] == prev:
                    continue
                arr.append(candidates[j])
                generate_combinations(j+1, arr, curr_total+candidates[j])
                arr.pop()
                prev = candidates[j]

        res = []
        candidates.sort()
        generate_combinations(0, [], 0)
        return res
```
#### - CPP Solution
```cpp
class Solution {
    set<vector<int>> res;

    void generate_combinations(int i, vector<int >arr, int curr_total, vector<int>& candidates, int target) {
        if (curr_total == target) {
            sort(arr.begin(), arr.end());
            res.insert(arr);
            return;
        }
        if (curr_total > target)
            return;
        int prev = -1;
        for (int j=i; j<candidates.size(); j++) {
            if (candidates[j] == prev)
                continue;
            arr.push_back(candidates[j]);
            generate_combinations(j+1, arr, curr_total+candidates[j], candidates, target);
            arr.pop_back();
            prev = candidates[j];
        }
    }
public:
    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        generate_combinations(0, {}, 0, candidates, target);
        vector<vector<int>> ans(res.begin(), res.end());
        return ans;
    }
};
```

### combination sum iii:
Problem Link: https://leetcode.com/problems/combination-sum-iii

#### - Python Solution
```python
class Solution:
    def combinationSum3(self, k: int, n: int) -> List[List[int]]:
        def generate_combinations(p, arr, curr_total):
            if len(arr) == k and curr_total == n:
                res.append(arr[:])
                return
            if sum(arr) > n:
                return
            for i in range(p, min(10, n+1)):
                arr.append(i)
                generate_combinations(i+1, arr, curr_total+i)
                arr.pop()

        res = []
        generate_combinations(1, [], 0)
        return res
```
#### - CPP Solution
```cpp
class Solution {
    vector<vector<int>> res;

    void generate_combinations(int p, vector<int> arr, int curr_total, int n, int k) {
        if (arr.size() == k and curr_total == n) {
            res.push_back(arr);
            return;
        }
        if (curr_total > n) {
            return;
        }
        for (int i=p; i<min(10, n+1); i++) {
            arr.push_back(i);
            generate_combinations(i+1, arr, curr_total+i, n, k);
            arr.pop_back();
        }
    }
public:
    vector<vector<int>> combinationSum3(int k, int n) {
        generate_combinations(1, {}, 0, n, k);
        return res;
    }
};
```

### generate parentheses:
Problem Link: https://leetcode.com/problems/generate-parentheses

#### - Python Solution
```python
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        def generate(cnt_open, cnt_close, s):
            if cnt_open == cnt_close == n:
                res.append(s)
                return
            if cnt_open < n:
                generate(cnt_open+1, cnt_close, s+'(')
            if cnt_close < cnt_open:
                generate(cnt_open, cnt_close+1, s+')')

        res = []
        generate(0, 0, '')
        return res
```
#### - CPP Solution
```cpp
class Solution {
    vector<string> res;

    void generate(int cnt_open, int cnt_close, string s, const int &n) {
        if (cnt_open == cnt_close and cnt_close == n) {
            res.push_back(s);
            return;
        }
        if (cnt_open < n)
            generate(cnt_open+1, cnt_close, s+"(", n);
        if (cnt_close < cnt_open)
            generate(cnt_open, cnt_close+1, s+")", n);
    }
public:
    vector<string> generateParenthesis(int n) {
        generate(0, 0, "", n);
        return res;
    }
};
```

### target sum:
Problem Link: https://leetcode.com/problems/target-sum

#### - Python Solution
```python
class Solution:
    def findTargetSumWays(self, nums: List[int], target: int) -> int:
        def dp(i, curr_total):
            if i == len(nums):
                return curr_total == target
            if memo[i][curr_total+N] != -1:
                return memo[i][curr_total+N]
            memo[i][curr_total+N] = dp(i+1, curr_total+nums[i]) + \
                                    dp(i+1, curr_total-nums[i])
            return memo[i][curr_total+N]

        N = int(2e4+3)
        memo = [[-1 for i in range(N*2)] for j in range(23)]
        return dp(0, 0)
```
#### - CPP Solution
```cpp
class Solution {
    static const int N = 2e4+3;
    int memo[23][N*2];

    int dp(int i, int curr_total, const vector<int>& nums, const int &target) {
        if (i == nums.size())
            return curr_total == target;
        if (memo[i][curr_total+N] != -1)
            return memo[i][curr_total+N];
        memo[i][curr_total+N] = dp(i+1, curr_total+nums[i], nums, target) +
                                dp(i+1, curr_total-nums[i], nums, target);
        return memo[i][curr_total+N];
    }
public:
    int findTargetSumWays(vector<int>& nums, int target) {
        memset(memo, -1, sizeof memo);
        return dp(0, 0, nums, target);
    }
};
```

### palindrome partitioning:
Problem Link: https://leetcode.com/problems/palindrome-partitioning

#### - Python Solution
```python
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        def is_palindrome(s):
            return s == s[::-1]

        def dfs(i):
            if i == len(s):
                res.append(curr_parts[:])
                return
            for j in range(i, len(s)):
                if is_palindrome(s[i:j+1]):
                    curr_parts.append(s[i:j+1])
                    dfs(j+1)
                    curr_parts.pop()

        res = []
        curr_parts = []
        dfs(0)
        return res
```
#### - CPP Solution
```cpp
class Solution {
    vector<vector<string>> res;
    vector<string> curr_parts;

    bool is_palindrome(string s) {
        string t = s;
        reverse(t.begin(), t.end());
        return s == t;
    }
    void dfs(int i, const string &s) {
        if (i == s.size()) {
            res.push_back(curr_parts);
            return;
        }
        for (int j=i; j<s.size(); j++) {
            if (is_palindrome(s.substr(i, j-i+1))) {
                curr_parts.push_back(s.substr(i, j-i+1));
                dfs(j+1, s);
                curr_parts.pop_back();
            }
        }
    }
public:
    vector<vector<string>> partition(string s) {
        dfs(0, s);
        return res;
    }
};
```

### letter combinations of a phone number:
Problem Link: https://leetcode.com/problems/letter-combinations-of-a-phone-number

#### - Python Solution
```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        def generate_letters(i, curr_s):
            if len(curr_s) == len(digits):
                res.append(curr_s)
                return
            for j in digits_chars[digits[i]]:
                generate_letters(i+1, curr_s+j)

        res = []
        digits_chars = {'2':'abc', '3':'def', '4':'ghi', '5':'jkl',
                        '6':'mno', '7':'pqrs', '8':'tuv', '9':'wxyz'}
        if digits:
            generate_letters(0, '')
        return res
```
#### - CPP Solution
```cpp
class Solution {
    vector<string> res;
    map<char, string> digits_chars = {{'2',"abc"}, {'3',"def"}, {'4',"ghi"}, {'5',"jkl"},
                                      {'6',"mno"}, {'7',"pqrs"}, {'8',"tuv"}, {'9',"wxyz"}};

    void generate_letters(int i, string curr_s, const string &digits) {
        if (curr_s.size() == digits.size()) {
            res.push_back(curr_s);
            return;
        }
        for (char j : digits_chars[digits[i]])
            generate_letters(i+1, curr_s+j, digits);
    }
public:
    vector<string> letterCombinations(string digits) {
        if (digits != "")
            generate_letters(0, "", digits);
        return res;
    }
};
```

### generalized abbreviation:
Problem Link: https://leetcode.com/problems/generalized-abbreviation

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### house robber:
Problem Link: https://leetcode.com/problems/house-robber

#### - Python Solution
```python
class Solution:
    def rob(self, nums: List[int]) -> int:
        res1, res2 = 0, 0
        for i in nums:
            temp = max(res1+i, res2)
            res1 = res2
            res2 = temp
        return res2
```
#### - CPP Solution
```cpp
class Solution {
public:
    int rob(vector<int>& nums) {
        int res1 = 0, res2 = 0;
        for (int i : nums) {
            int temp = max(res1+i, res2);
            res1 = res2;
            res2 = temp;
        }
        return res2;
    }
};
```

### house robber ii:
Problem Link: https://leetcode.com/problems/house-robber-ii

#### - Python Solution
```python
class Solution:
    def rob(self, nums: List[int]) -> int:
        def rob_subarray(nums):
            res1, res2 = 0, 0
            for i in nums:
                temp = max(res1+i, res2)
                res1 = res2
                res2 = temp
            return res2

        if len(nums) == 1:
            return nums[0]
        return max(rob_subarray(nums[1:]), rob_subarray(nums[:-1]))
```
#### - CPP Solution
```cpp
class Solution {
    int rob_subarray(vector<int> nums) {
        int res1 = 0, res2 = 0;
        for (int i : nums) {
            int temp = max(res1+i, res2);
            res1 = res2;
            res2 = temp;
        }
        return res2;
    }
public:
    int rob(vector<int>& nums) {
        if (nums.size() == 1)
            return nums[0];
        return max(rob_subarray({nums.begin()+1, nums.end()}),
                   rob_subarray({nums.begin(), nums.end()-1}));
    }
};
```

### coin change:
Problem Link: https://leetcode.com/problems/coin-change

#### - Python Solution
```python
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        dp = [int(1e4+3)] * (amount+1)
        dp[0] = 0
        for i in range(1, amount+1):
            for c in coins:
                if i - c >= 0:
                    dp[i] = min(dp[i], dp[i-c]+1)
        if dp[amount] == int(1e4+3):
            dp[amount] = -1
        return dp[amount]
```
#### - CPP Solution
```cpp
class Solution {
public:
    int coinChange(vector<int>& coins, int amount) {
        vector<int> dp(amount+1, int(1e4+3));
        dp[0] = 0;
        for (int i=1; i<amount+1; i++) {
            for (int c : coins) {
                if (i - c >= 0)
                    dp[i] = min(dp[i], dp[i-c]+1);
            }
        }
        if (dp[amount] == int(1e4+3))
            dp[amount] = -1;
        return dp[amount];
    }
};
```

### maximum product subarray:
Problem Link: https://leetcode.com/problems/maximum-product-subarray

#### - Python Solution
```python
class Solution:
    def maxProduct(self, nums: List[int]) -> int:
        res = max(nums)
        curr_min, curr_max = 1, 1
        for i in nums:
            prev_min, prev_max = curr_min, curr_max
            curr_min = min(prev_min, prev_max, 1) * i
            curr_max = max(prev_min, prev_max, 1) * i
            res = max(res, curr_min, curr_max)
        return res
```
#### - CPP Solution
```cpp
class Solution {
public:
    int maxProduct(vector<int>& nums) {
        int res = *max_element(nums.begin(), nums.end());
        int curr_min = 1, curr_max = 1;
        int prev_min = 1, prev_max = 1;
        for (int i : nums) {
            prev_min = curr_min, prev_max = curr_max;
            curr_min = min(min(prev_min, prev_max), 1) * i;
            curr_max = max(max(prev_min, prev_max), 1) * i;
            res = max(res, max(curr_min, curr_max));
        }
        return res;
    }
};
```

### longest increasing subsequence:
Problem Link: https://leetcode.com/problems/longest-increasing-subsequence

#### - Python Solution
```python
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        res = [1] * len(nums)
        for i in range(len(nums)-1, -1, -1):
            for j in range(i+1, len(nums)):
                if nums[j] > nums[i]:
                    res[i] = max(res[i], res[j]+1)
        return max(res)
```
#### - CPP Solution
```cpp
class Solution {
public:
    int lengthOfLIS(vector<int>& nums) {
        vector<int> res(nums.size(), 1);
        for (int i=nums.size()-1; i>-1; i--) {
            for (int j=i+1; j<nums.size(); j++) {
                if (nums[j] > nums[i])
                    res[i] = max(res[i], res[j]+1);
            }
        }
        return *max_element(res.begin(), res.end());
    }
};
```

### longest palindromic substring:
Problem Link: https://leetcode.com/problems/longest-palindromic-substring

#### - Python Solution
```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        def get_longest(size_type):
            res = ''
            res_len = 0
            for i in range(len(s)):
                l, r = i, i+size_type
                while l >= 0 and r < len(s) and s[l] == s[r]:
                    if res_len < r-l+1:
                        res = s[l:r+1]
                        res_len = r-l+1
                    l -= 1
                    r += 1
            return res

        res1 = get_longest(0)
        res2 = get_longest(1)
        return res1 if len(res1) > len(res2) else res2
```
#### - CPP Solution
```cpp
class Solution {
    string get_longest(bool size_type, string &s) {
        string res = "";
        int res_len = 0;
        int l, r;
        for (int i=0; i<s.size(); i++) {
            l = i, r = i+size_type;
            while (l >= 0 and r < s.size() and s[l] == s[r]) {
                if (res_len < r-l+1) {
                    res = s.substr(l, r-l+1);
                    res_len = r-l+1;
                }
                l --;
                r ++;
            }
        }
        return res;
    }
public:
    string longestPalindrome(string s) {
        string res1 = get_longest(0, s);
        string res2 = get_longest(1, s);
        return (res1.size() > res2.size())? res1 : res2;
    }
};
```

### word break:
Problem Link: https://leetcode.com/problems/word-break

#### - Python Solution
```python
class Solution:
    def wordBreak(self, s: str, wordDict: List[str]) -> bool:
        dp = [0] * (len(s)+1)
        dp[len(s)] = 1
        for i in range(len(s)-1, -1, -1):
            for w in wordDict:
                if i+len(w) <= len(s) and s[i:i+len(w)] == w and dp[i+len(w)]:
                    dp[i] = dp[i+len(w)]
        return dp[0]
```
#### - CPP Solution
```cpp
class Solution {
public:
    bool wordBreak(string s, vector<string>& wordDict) {
        vector<int> dp(s.size()+1, 0);
        dp[s.size()] = 1;
        for (int i=s.size()-1; i>-1; i--) {
            for (string w : wordDict) {
                if (i+w.size() <= s.size() and s.substr(i, w.size()) == w and dp[i+w.size()])
                    dp[i] = dp[i+w.size()];
            }
        }
        return dp[0];
    }
};
```

### combination sum iv:
Problem Link: https://leetcode.com/problems/combination-sum-iv

#### - Python Solution
```python
class Solution:
    def combinationSum4(self, nums: List[int], target: int) -> int:
        N = int(1e3+1)
        dp = [0] * (2*N)
        dp[N] = 1
        for i in range(1, target+1):
            for j in nums:
                dp[i+N] += dp[i-j+N]
        return dp[target+N]
```
#### - CPP Solution
```cpp
class Solution {
    static const int N = int(1e3+1);
    int dp[2*N] = {0};
public:
    int combinationSum4(vector<int>& nums, int target) {
        dp[N] = 1;
        for (int i=1; i<target+1; i++) {
            for (int j : nums) {
                dp[i+N] += dp[i-j+N];
            }
        }
        return dp[target+N];
    }
};
```
`TODO` RUN-TIME ERROR

### decode ways:
Problem Link: https://leetcode.com/problems/decode-ways

#### - Python Solution
```python
class Solution:
    def numDecodings(self, s: str) -> int:
        def dp(i):
            if memo[i] != -1:
                return memo[i]
            if s[i] == '0':
                return 0
            res = dp(i+1)
            if i+1 < len(s) and 10 <= int(s[i]+s[i+1]) <= 26:
                res += dp(i+2)
            memo[i] = res
            return memo[i]

        memo = [-1] * (len(s)+1)
        memo[len(s)] = 1
        return dp(0)
```
#### - CPP Solution
```cpp
class Solution {
    int memo[101];

    int dp(int i, string &s) {
        if (memo[i] != -1)
            return memo[i];
        if (s[i] == '0')
            return 0;
        int res = dp(i+1, s);
        if (i+1 < s.size() and 10 <= stoi(s.substr(i, 2)) and stoi(s.substr(i, 2)) <= 26)
            res += dp(i+2, s);
        memo[i] = res;
        return memo[i];
    }
public:
    int numDecodings(string s) {
        memset(memo, -1, sizeof memo);
        memo[s.size()] = 1;
        return dp(0, s);
    }
};
```

### unique paths:
Problem Link: https://leetcode.com/problems/unique-paths

#### - Python Solution
```python
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        memo = [[0 for i in range(n)] for j in range(m)]
        memo[m-1] = [1] * n
        for i in range(m-2, -1, -1):
            memo[i][n-1] = 1
            for j in range(n-2, -1, -1):
                memo[i][j] = memo[i][j+1] + memo[i+1][j]
        return memo[0][0]
```
#### - CPP Solution
```cpp
class Solution {
public:
    int uniquePaths(int m, int n) {
        vector<vector<int>> memo(m, vector<int>(n, 0));
        fill(memo[m-1].begin(), memo[m-1].end(), 1);
        for (int i=m-2; i>-1; i--) {
            memo[i][n-1] = 1;
            for (int j=n-2; j>-1; j--) {
                memo[i][j] = memo[i][j+1] + memo[i+1][j];
            }
        }
        return memo[0][0];
    }
};
```

### Jump Game:
Problem Link: https://leetcode.com/problems/jump-game

#### - Python Solution
```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        res = len(nums)-1
        for i in range(len(nums)-1, -1, -1):
            if i + nums[i] >= res:
                res = i
        return res == 0
```
#### - CPP Solution
```cpp
class Solution {
public:
    bool canJump(vector<int>& nums) {
        int res = nums.size()-1;
        for (int i=nums.size()-1; i>-1; i--) {
            if (i + nums[i] >= res)
                res = i;
        }
        return res == 0;
    }
};
```

### palindromic substrings:
Problem Link: https://leetcode.com/problems/palindromic-substrings

#### - Python Solution
```python
class Solution:
    def countSubstrings(self, s: str) -> int:
        def count_pali(s, l, r):
            res = 0
            while l >=0 and r < len(s) and s[l] == s[r]:
                l -= 1
                r += 1
                res += 1
            return res

        res = 0
        for i in range(len(s)):
            res += count_pali(s, i, i)
            res += count_pali(s, i, i+1)
        return res
```
#### - CPP Solution
```cpp
class Solution {
    int count_pali(string s, int l, int r) {
        int res = 0;
        while (l >=0 and r < s.size() and s[l] == s[r]) {
            l --;
            r ++;
            res ++;
        }
        return res;
    }
public:
    int countSubstrings(string s) {
        int res = 0;
        for (int i=0; i<s.size(); i++) {
            res += count_pali(s, i, i);
            res += count_pali(s, i, i+1);
        }
        return res;
    }
};
```

### number of longest increasing subsequence:
Problem Link: https://leetcode.com/problems/number-of-longest-increasing-subsequence

#### - Python Solution
```python
class Solution:
    def findNumberOfLIS(self, nums: List[int]) -> int:
        dp = {}
        len_lis, res = 0, 0
        for i in range(len(nums) - 1, -1, -1):
            max_len, max_cnt = 1, 1
            for j in range(i + 1, len(nums)):
                if nums[j] <= nums[i]:
                    continue
                length, count = dp[j]
                if length + 1 > max_len:
                    max_len, max_cnt = length + 1, count
                elif length + 1 == max_len:
                    max_cnt += count
            if max_len > len_lis:
                len_lis, res = max_len, max_cnt
            elif max_len == len_lis:
                res += max_cnt
            dp[i] = [max_len, max_cnt]
        return res
```
#### - CPP Solution
```cpp
class Solution {
public:
    int findNumberOfLIS(vector<int>& nums) {
        map<int, pair<int, int>> dp;
        int len_lis = 0, res = 0;
        for (int i=nums.size()-1; i>-1; i--) {
            int max_len = 1, max_cnt = 1;
            for (int j=i+1; j<nums.size(); j++) {
                if (nums[j] <= nums[i])
                    continue;
                auto [length, count] = dp[j];
                if (length + 1 > max_len)
                    max_len = length + 1, max_cnt = count;
                else if (length + 1 == max_len)
                    max_cnt += count;
            }
            if (max_len > len_lis)
                len_lis = max_len, res = max_cnt;
            else if (max_len == len_lis)
                res += max_cnt;
            dp[i] = {max_len, max_cnt};
        }
        return res;
    }
};
```
