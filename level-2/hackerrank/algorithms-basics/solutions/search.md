<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="80" src="/logos/hackerrank.png"></img></a>

# HackerRank OJ - Algorithms Basics <br> Search `20 problems`

## Ice Cream Parlor
Problem Link: https://hackerrank.com/challenges/icecream-parlor/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def icecreamParlor(m, arr):
    for i in range(len(arr)):
        for j in range(i+1, len(arr)):
            if arr[i] + arr[j] == m:
                return i + 1, j + 1
    return -1, -1
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
vector<int> icecreamParlor(int m, vector<int> arr) {
    for (int i=0; i<size(arr); i++) {
        for (int j=i+1; j<size(arr); j++) {
            if (arr[i] + arr[j] == m)
                return {i + 1, j + 1};
        }
    }
    return {-1, -1};
}
```

</details>

## Missing Numbers
Problem Link: https://hackerrank.com/challenges/missing-numbers/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def missingNumbers(arr, brr):
    m = max(arr + brr) + 1
    cnt = [0] * m
    for i in arr:
        cnt[i] += 1
    for i in brr:
        cnt[i] -= 1
    res = sorted([i for i in range(len(cnt)) if cnt[i] != 0])
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
vector<int> missingNumbers(vector<int> arr, vector<int> brr) {
    int m = max(*max_element(arr.begin(), arr.end()),
                *max_element(brr.begin(), brr.end())) + 1;
    vector<int> cnt(m, 0);
    for (int &i : arr)
        cnt[i] ++;
    for (int &i : brr)
        cnt[i] --;
    vector<int> res;
    for (int i=0; i<size(cnt); i++)
        if (cnt[i] != 0)
            res.push_back(i);
    sort(res.begin(), res.end());
    return res;
}
```

</details>

## Sherlock and Array
Problem Link: https://hackerrank.com/challenges/sherlock-and-array/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def balancedSums(arr):
    left = 0
    right = sum(arr)
    for i in arr:
        right -= i
        if right == left:
            return 'YES'
        left += i
    return 'NO'
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
string balancedSums(vector<int> arr) {
    int left = 0;
    int right = accumulate(arr.begin(), arr.end(), 0);
    for (int &i : arr) {
        right -= i;
        if (right == left)
            return "YES";
        left += i;
    }
    return "NO";
}
```

</details>

## Hackerland Radio Transmitters
Problem Link: https://hackerrank.com/challenges/hackerland-radio-transmitters/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def binary_search(a, x, l=0):
    r = len(a) - 1
    while l <= r:
        m = (l + r) // 2
        if a[m] > x:
            r = m - 1
        else:
            l = m + 1
    return l

def hackerlandRadioTransmitters(x, k):
    chunk = []
    x.sort()
    temp = [x[0]]
    for i in range(len(x)-1):
        if x[i+1] - x[i] <= k:
            temp.append(x[i+1])
        else:
            chunk.append(temp)
            temp = [x[i+1]]
    chunk.append(temp)
    res = 0
    for seg in chunk:
        while seg:
            i = binary_search(seg, seg[0]+k) - 1
            j = binary_search(seg, seg[i]+k, i+1)
            seg = seg[j:]
            res += 1
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int binary_search(vector<int> a, int x, int l=0) {
    int r = size(a) - 1;
    while (l <= r) {
        int m = (l + r) / 2;
        if (a[m] > x)
            r = m - 1;
        else
            l = m + 1;
    }
    return l;
}
int hackerlandRadioTransmitters(vector<int> x, int k) {
    vector<vector<int>> chunk;
    sort(x.begin(), x.end());
    vector<int> temp = {x[0]};
    for (int i=0; i<size(x)-1; i++) {
        if (x[i+1] - x[i] <= k)
            temp.push_back(x[i+1]);
        else {
            chunk.push_back(temp);
            temp = {x[i+1]};
        }
    }
    chunk.push_back(temp);
    int res = 0;
    for (auto &seg : chunk) {
        while (size(seg)) {
            cout << size(seg) << endl;
            int i = binary_search(seg, seg[0]+k) - 1;
            int j = binary_search(seg, seg[i]+k, i+1);
            seg.erase(seg.begin(), seg.begin()+j);
            res ++;
        }
    }
    return res;
}
```

</details>

## Gridland Metro
Problem Link: https://hackerrank.com/challenges/gridland-metro/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def is_subset(a, b):
    min_val, max_val = min(a[0], b[0]), max(a[1], b[1])
    return b[0] == min_val and b[1] == max_val or \
           a[0] == min_val and a[1] == max_val

def is_overlap(a, b):
    return b[0] < a[0] and a[0] <= b[1] < a[1] or \
           a[0] < b[0] and b[0] <= a[1] < b[1]

def union_seg(a, b):
    return [min(a[0], b[0]), max(a[1], b[1])]

def gridlandMetro(n, m, k, track):
    trains = {}
    for r, c1, c2 in track:
        if r not in trains:
            trains[r] = []
        row = trains[r]
        new_train = [c1, c2]
        overlapping = False
        for i in range(len(row)):
            if is_overlap(row[i], new_train) or \
               is_subset(row[i], new_train):
                row[i] = union_seg(row[i], new_train)
                overlapping = True
                break
        if not overlapping:
            row.append(new_train)
    res = 0
    for _, row in trains.items():
        for train in row:
            res += train[1] - train[0] + 1
    return n * m - res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
bool is_subset(vector<int> &a, vector<int> &b) {
    int min_val = min(a[0], b[0]), max_val = max(a[1], b[1]);
    return b[0] == min_val and b[1] == max_val or
           a[0] == min_val and a[1] == max_val;
}
bool is_overlap(vector<int> &a, vector<int> &b) {
    return b[0] < a[0] and a[0] <= b[1] and b[1] < a[1] or
           a[0] < b[0] and b[0] <= a[1] and a[1] < b[1];
}
vector<int> union_seg(vector<int> &a, vector<int> &b) {
    return {min(a[0], b[0]), max(a[1], b[1])};
}
long long gridlandMetro(int n, int m, int k, vector<vector<int>> track) {
    map<int, vector<vector<int>>> trains;
    for (auto &it : track) {
        auto &row = trains[it[0]];
        vector<int> new_train = {it[1], it[2]};
        bool overlapping = false;
        for (int i=0; i<size(row); i++) {
            if (is_overlap(row[i], new_train) or
                is_subset(row[i], new_train)) {
                row[i] = union_seg(row[i], new_train);
                overlapping = true;
                break;
            }
        }
        if (not overlapping)
            row.push_back(new_train);
    }
    long long res = 0;
    for (auto &row : trains)
        for (auto &train : row.second)
            res += train[1] - train[0] + 1;
    return 1LL * n * m - res;
}
```

</details>

## KnightL on a Chessboard
Problem Link: https://hackerrank.com/challenges/knightl-on-chessboard/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
dx = [1, 1, -1, -1]
dy = [1, -1, 1, -1]

def knightl_helper(n, i, j):
    grid = [[2e9 for i in range(n)] for j in range(n)]
    que = []
    que.append((0, 0))
    grid[0][0] = 0
    while que:
        x, y = que.pop()
        curr = grid[x][y] + 1
        next_pos = []
        for k in range(4):
            next_pos.append((x + i*dx[k], y + j*dy[k]))
            next_pos.append((x + j*dx[k], y + i*dy[k]))
        for x, y in next_pos:
            if 0 <= x <= n - 1 and 0 <= y <= n - 1:
                if grid[x][y] > curr:
                    grid[x][y] = curr
                    que.append((x, y))
    if grid[n-1][n-1] != 2e9:
        return grid[n-1][n-1]
    return -1

def knightlOnAChessboard(n):
    res = [[-1 for i in range(n-1)] for j in range(n-1)]
    for i in range(1, n):
        for j in range(1, n):
                res[i-1][j-1] = knightl_helper(n, i, j)
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
const int dx[] = {1, 1, -1, -1};
const int dy[] = {1, -1, 1, -1};

int knightl_helper(int n, int i, int j) {
    vector<vector<int>> grid(n, vector<int>(n, 2e9));
    queue<pair<int, int>> que;
    que.push({0, 0});
    grid[0][0] = 0;
    while (!que.empty()) {
        pair<int, int> pos = que.front();
        que.pop();
        int curr = grid[pos.first][pos.second] + 1;
        vector<pair<int, int>> next_pos;
        for (int k = 0; k < 4; k++) {
            next_pos.push_back({pos.first + i*dx[k], pos.second + j*dy[k]});
            next_pos.push_back({pos.first + j*dx[k], pos.second + i*dy[k]});
        }
        for (auto &[x, y] : next_pos) {
            if (0 <= x and x <= n - 1 and 0 <= y and y <= n - 1) {
                if (grid[x][y] > curr) {
                    grid[x][y] = curr;
                    que.push({x, y});
                }
            }
        }
    }
    if (grid[n-1][n-1] != 2e9)
        return grid[n-1][n-1];
    return -1;
}
vector<vector<int>> knightlOnAChessboard(int n) {
    vector<vector<int>> res(n-1, vector<int>(n-1, -1));
    for (int i=1; i<n; i++)
        for (int j=1; j<n; j++)
            res[i-1][j-1] = knightl_helper(n, i, j);
    return res;
}
```

</details>

## Minimum Loss
Problem Link: https://hackerrank.com/challenges/minimum-loss/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def minimumLoss(price):
    arr = []
    for i in range(len(price)):
        arr.append((price[i], i))
    arr.sort()
    res = 1e16
    for i in range(1, len(price)):
        if arr[i][1] < arr[i-1][1]:
            res = min(res, abs(arr[i][0] - arr[i-1][0]))
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int minimumLoss(vector<long> price) {
    vector<pair<long, int>> arr(size(price));
    for (int i=0; i<size(price); i++)
        arr[i] = {price[i], i};
    sort(arr.begin(), arr.end());
    long res = 1e16;
    for (int i=1; i<size(price); i++)
        if (arr[i].second < arr[i-1].second)
            res = min(res, abs(arr[i].first - arr[i-1].first));
    return res;
}
```

</details>

## Pairs
Problem Link: https://hackerrank.com/challenges/pairs/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def pairs(k, arr):
    res = 0
    distinct = set(arr)
    for i in arr:
        if i - k in distinct:
            res += 1
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int pairs(int k, vector<int> arr) {
    int res = 0;
    set<int> distinct(arr.begin(), arr.end());
    for (int &i : arr)
        if (distinct.find(i - k) != distinct.end())
            res ++;
    return res;
}
```

</details>

## Connected Cells in a Grid
Problem Link: https://hackerrank.com/challenges/connected-cell-in-a-grid/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
dx = [1, 1, -1, -1, 1, -1, 0, 0]
dy = [1, -1, 1, -1, 0, 0, 1, -1]

def dfs(A, i, j, n, m):
    A[i][j] = -1
    res = 1
    for k in range(8):
        x, y = i+dx[k], j+dy[k]
        if x >= 0 and y >= 0 and x < n and y < m and A[x][y] == 1:
            res += dfs(A, x, y, n, m)
    return res

def connectedCell(matrix):
    n, m = len(matrix), len(matrix[0])
    res = 0
    for i in range(n):
        for j in range(m):
            if matrix[i][j] == 1:
                res = max(res, dfs(matrix, i, j, n, m))
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
const int dx[] = {1, 1, -1, -1, 1, -1, 0, 0};
const int dy[] = {1, -1, 1, -1, 0, 0, 1, -1};

int dfs(vector<vector<int>> &A, int i, int j, int n, int m) {
    A[i][j] = -1;
    int res = 1;
    for (int k=0; k<8; k++) {
        int x = i+dx[k], y = j+dy[k];
        if (x >= 0 and y >= 0 and x < n and y < m and A[x][y] == 1)
            res += visdfsit(A, x, y, n, m);
    }
    return res;
}
int connectedCell(vector<vector<int>> matrix) {
    int n = size(matrix), m = size(matrix[0]);
    int res = 0;
    for (int i = 0; i < n; i++)
        for (int j = 0; j < m; j++)
            if (matrix[i][j] == 1)
                res = max(res, dfs(matrix, i, j, n, m));
    return res;
}
```

</details>

## Short Palindrome
Problem Link: https://hackerrank.com/challenges/short-palindrome/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def shortPalindrome(s):
    mod = int(1e9 + 7)
    res = 0
    freq = [0] * 26
    tripfreq = [0] * 26
    pairfreq = [[0] * 26 for i in range(26)]
    for c in s:
        idx = ord(c) - ord('a')
        res = (res + tripfreq[idx]) % mod
        for i in range(26):
            tripfreq[i] = (tripfreq[i] + pairfreq[i][idx]) % mod;
            pairfreq[i][idx] = (pairfreq[i][idx] + freq[i]) % mod;
        freq[idx] += 1
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int shortPalindrome(string s) {
    int mod = 1e9 + 7;
    int res = 0;
    vector<int> freq(26, 0);
    vector<int> tripfreq(26, 0);
    vector<vector<int>> pairfreq(26, vector<int>(26));
    for (char &c : s) {
        int idx = c - 'a';
        res = (res + tripfreq[idx]) % mod;
        for (int i=0; i<26; i++) {
            tripfreq[i] = (tripfreq[i] + pairfreq[i][idx]) % mod;
            pairfreq[i][idx] = (pairfreq[i][idx] + freq[i]) % mod;
        }
        freq[idx] ++;
    }
    return res;
}
```

</details>

## Count Luck
Problem Link: https://www.hackerrank.com/challenges/count-luck/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
dx = [1, -1, 0, 0]
dy = [0, 0, 1, -1]

def dfs(i, j, matrix, visited, des):
    if (i, j) == des:
        return True
    visited.add((i, j))
    for w in range(4):
        x, y = i+dx[w], j+dy[w]
        if 0 <= x < n and 0 <= y < m and matrix[x][y] != 'X' \
           and (x, y) not in visited and dfs(x, y, matrix, visited, des):
            return True
    visited.remove((i, j))
    return False

def countLuck(matrix, k):
    n, m = len(matrix), len(matrix[0])
    src, des = (0, 0), (0, 0)
    for i in range(n):
        for j in range(m):
            if matrix[i][j] == 'M':
                src = (i, j)
            if matrix[i][j] == '*':
                des = (i, j)
    visited = set()
    dfs(src[0], src[1], matrix, visited, des)
    res = 0
    for i, j in visited:
        for w in range(4):
            x, y = i+dx[w], j+dy[w]
            if 0 <= x < n and 0 <= y < m and \
               matrix[x][y] == '.' and \
               (x, y) not in visited:
                res += 1
                break
    return ('Impressed' if res == k else 'Oops!')
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
const int dx[] = {1, -1, 0, 0};
const int dy[] = {0, 0, 1, -1};
int n, m;

bool dfs(int i, int j, vector<string> &matrix, set<pair<int, int>> &visited, pair<int, int> des) {
    if (make_pair(i, j) == des)
        return true;
    visited.insert({i, j});
    for (int k=0; k<4; k++) {
        int x = i+dx[k], y = j+dy[k];
        if (0 <= x and x < n and 0 <= y and y < m and
            visited.find({x, y}) == visited.end() and 
            matrix[x][y] != 'X' and dfs(x, y, matrix, visited, des))
            return true;
    }
    visited.erase(visited.find({i, j}));
    return false;
}
string countLuck(vector<string> matrix, int k) {
    n = size(matrix), m = size(matrix[0]);
    pair<int, int> src, des;
    for (int i=0; i<n; i++) {
        for (int j=0; j<m; j++) {
            if (matrix[i][j] == 'M')
                src = make_pair(i, j);
            if (matrix[i][j] == '*')
                des = make_pair(i, j);
        }
    }
    set<pair<int, int>> visited;
    dfs(src.first, src.second, matrix, visited, des);
    int res = 0;
    for (auto &[i, j] : visited) {
        for (int k=0; k<4; k++) {
            int x = i+dx[k], y = j+dy[k];
            if (0 <= x and x < n and 0 <= y and y < m and
                matrix[x][y] == '.' and
                visited.find({x, y}) == visited.end()) {
                res ++;
                break;
            }
        }
    }
    return (res == k? "Impressed" : "Oops!");
}
```

</details>

## Cut the Tree
Problem Link: https://www.hackerrank.com/challenges/cut-the-tree/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## Gena Playing Hanoi
Problem Link: https://www.hackerrank.com/challenges/gena/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## Beautiful Quadruples
Problem Link: https://www.hackerrank.com/challenges/xor-quadruples/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def beautifulQuadruples(a, b, c, d):
    a, b, c, d = sorted([a, b, c, d])
    N = int(3e3+3)
    total = [0] * N
    cnt = [[0 for j in range(1<<12)] for i in range(N)]
    for i in range(1, a+1):
        for j in range(i, b+1):
            total[j] += 1
            cnt[j][i^j] += 1
    for i in range(1, N):
        total[i] += total[i-1]
        for j in range(1<<12):
            cnt[i][j] += cnt[i-1][j]
    res = 0
    for i in range(1, c+1):
        for j in range(i, d+1):
            res += total[i] - cnt[i][i^j]
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
long long beautifulQuadruples(int a, int b, int c, int d) {
    vector<int> temp = {a, b, c, d};
    sort(temp.begin(), temp.end());
    a = temp[0], b = temp[1], c = temp[2], d = temp[3];
    const int N = 3e3+3;
    vector<int> total(N, 0);
    vector<vector<int> > cnt(N, vector<int>(1<<12, 0));
    for (int i=1; i<a+1; i++) {
        for (int j=i; j<b+1; j++) {
            total[j] ++;
            cnt[j][i^j] ++;
        }
    }
    for (int i=1; i<N; i++) {
        total[i] += total[i-1];
        for (int j=0; j<(1<<12); j++)
            cnt[i][j] += cnt[i-1][j];
    }
    long long res = 0;
    for (int i=1; i<c+1; i++)
        for (int j=i; j<d+1; j++)
            res += total[i] - cnt[i][i^j];
    return res;
}
```

</details>

## Red Knight's Shortest Path
Problem Link: https://www.hackerrank.com/challenges/red-knights-shortest-path/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def printShortestPath(n, i_start, j_start, i_end, j_end):
    end = (i_end, j_end)
    visited = set()
    visited.add((i_start, j_start))
    que = [(i_start, j_start, '')]
    cnt = 0
    steps = [('UL', -2, -1), 
             ('UR', -2,  1), 
             ('R' ,  0,  2), 
             ('LR',  2,  1), 
             ('LL',  2, -1), 
             ('L' ,  0, -2)]
    while que:
        cnt += 1
        m = len(que)
        while m:
            m -= 1
            i, j, path = que.pop(0)
            for d, stepx, stepy in steps:
                x = i + stepx
                y = j + stepy
                if (x, y) == end:
                    path += ' ' + d 
                    return str(cnt) + '\n' + path[1:]
                if 0 <= x < n and 0 <= y < n and (x, y) not in visited:
                    visited.add((x, y))
                    que.append((x, y, path+' '+d))
    return 'Impossible'
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
string printShortestPath(int n, int i_start, int j_start, int i_end, int j_end) {
    pair<int, int> end = {i_end, j_end};
    set<pair<int, int>> visited;
    visited.insert({i_start, j_start});
    queue<tuple<int, int, string>> que;
    que.push({i_start, j_start, ""});
    int cnt = 0;
    vector<tuple<string, int, int>> steps = {{"UL", -2, -1}, 
                                             {"UR", -2,  1}, 
                                             {"R" ,  0,  2}, 
                                             {"LR",  2,  1}, 
                                             {"LL",  2, -1}, 
                                             {"L" ,  0, -2}};
    while (size(que)) {
        cnt ++;
        int m = size(que);
        while (m) {
            m --;
            auto [i, j, path] = que.front();
            que.pop();
            for (auto &[d, stepx, stepy] : steps) {
                int x = i + stepx;
                int y = j + stepy;
                if (make_pair(x, y) == end) {
                    path += ' ' + d;
                    return to_string(cnt) + '\n' + path.substr(1);
                }
                if (0 <= x and x < n and 0 <= y and y < n 
                    and visited.find({x, y}) == visited.end()) {
                    visited.insert({x, y});
                    que.push({x, y, path+' '+d});
                }
            }
        }
    }
    return "Impossible";
}
```

</details>

## Maximum Subarray Sum
Problem Link: https://www.hackerrank.com/challenges/maximum-subarray-sum/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## Maximizing Mission Points
Problem Link: https://www.hackerrank.com/challenges/maximizing-mission-points/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## Making Candies
Problem Link: https://www.hackerrank.com/challenges/making-candies/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## Bike Racers
Problem Link: https://www.hackerrank.com/challenges/bike-racers/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## Absolute Element Sums
Problem Link: https://www.hackerrank.com/challenges/playing-with-numbers/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>
