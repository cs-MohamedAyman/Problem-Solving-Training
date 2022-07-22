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
