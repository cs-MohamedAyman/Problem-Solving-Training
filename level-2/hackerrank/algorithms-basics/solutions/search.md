<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="80" src="/logos/hackerrank.png"></img></a>

# HackerRank OJ - Algorithms Basics <br> Search `20 problems`

## Ice Cream Parlor
Problem Link: https://www.hackerrank.com/challenges/icecream-parlor/problem

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
Problem Link: https://www.hackerrank.com/challenges/missing-numbers/problem

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
Problem Link: https://www.hackerrank.com/challenges/sherlock-and-array/problem

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
Problem Link: https://www.hackerrank.com/challenges/hackerland-radio-transmitters/problem

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
Problem Link: https://www.hackerrank.com/challenges/gridland-metro/problem

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
Problem Link: https://www.hackerrank.com/challenges/knightl-on-chessboard/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/search.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
dx = [1, 1, -1, -1]
dy = [1, -1, 1, -1]

def knightl_helper(n, i, j):
    grid = [[2e9 for i in range(n)] for j in range(n)]
    q = []
    q.append((0, 0))
    grid[0][0] = 0
    while q:
        x, y = q.pop()
        curr = grid[x][y] + 1
        next_pos = []
        for k in range(4):
            next_pos.append((x + i*dx[k], y + j*dy[k]))
            next_pos.append((x + j*dx[k], y + i*dy[k]))
        for x, y in next_pos:
            if 0 <= x <= n - 1 and 0 <= y <= n - 1:
                if grid[x][y] > curr:
                    grid[x][y] = curr
                    q.append((x, y))
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
int dx[] = {1, 1, -1, -1};
int dy[] = {1, -1, 1, -1};

int knightl_helper(int n, int i, int j) {
    vector<vector<int>> grid(n, vector<int>(n, 2e9));
    queue<pair<int, int>> q;
    q.push({0, 0});
    grid[0][0] = 0;
    while (!q.empty()) {
        pair<int, int> pos = q.front();
        q.pop();
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
                    q.push({x, y});
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
Problem Link: https://www.hackerrank.com/challenges/minimum-loss/problem

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
Problem Link: https://www.hackerrank.com/challenges/pairs/problem

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
Problem Link: https://www.hackerrank.com/challenges/connected-cell-in-a-grid/problem

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
int dx[] = {1, 1, -1, -1, 1, -1, 0, 0};
int dy[] = {1, -1, 1, -1, 0, 0, 1, -1};

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
Problem Link: https://www.hackerrank.com/challenges/short-palindrome/problem

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

## ProblemName
Problem Link: ProblemLink

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

## ProblemName
Problem Link: ProblemLink

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

## ProblemName
Problem Link: ProblemLink

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

## ProblemName
Problem Link: ProblemLink

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

## ProblemName
Problem Link: ProblemLink

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

## ProblemName
Problem Link: ProblemLink

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

## ProblemName
Problem Link: ProblemLink

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

## ProblemName
Problem Link: ProblemLink

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

## ProblemName
Problem Link: ProblemLink

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

## ProblemName
Problem Link: ProblemLink

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

## ProblemName
Problem Link: ProblemLink

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

## ProblemName
Problem Link: ProblemLink

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

## ProblemName
Problem Link: ProblemLink

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

## ProblemName
Problem Link: ProblemLink

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

## ProblemName
Problem Link: ProblemLink

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

## ProblemName
Problem Link: ProblemLink

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

## ProblemName
Problem Link: ProblemLink

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

## ProblemName
Problem Link: ProblemLink

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

## ProblemName
Problem Link: ProblemLink

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

## ProblemName
Problem Link: ProblemLink

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

