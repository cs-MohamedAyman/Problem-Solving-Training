<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="80" src="/logos/hackerrank.jpg"></img></a>

# HackerRank OJ - Data Structures - Stacks & Queues

## Equal Stacks
Problem Link: https://hackerrank.com/challenges/equal-stacks/problem

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def equalStacks(h1, h2, h3):
    s1, s2, s3 = [], [], []
    sum_h1, sum_h2, sum_h3 = 0, 0, 0;
    res = 0
    for i in range(len(h1)-1, -1, -1):
        s1.append(h1[i])
        sum_h1 += h1[i]
    for i in range(len(h2)-1, -1, -1):
        s2.append(h2[i])
        sum_h2 += h2[i]
    for i in range(len(h3)-1, -1, -1):
        s3.append(h3[i])
        sum_h3 += h3[i]
    res = min(sum_h1, sum_h2, sum_h3)
    while sum_h1 != sum_h2 or sum_h2 != sum_h3:
        while sum_h1 > res:
            sum_h1 -= s1[-1]
            s1.pop()
        res = min(sum_h1, sum_h2, sum_h3)
        while sum_h2 > res:
            sum_h2 -= s2[-1]
            s2.pop();
        res = min(sum_h1, sum_h2, sum_h3)
        while sum_h3 > res:
            sum_h3 -= s3[-1]
            s3.pop()
        res = min(sum_h1, sum_h2, sum_h3)
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int equalStacks(vector<int> h1, vector<int> h2, vector<int> h3) {
    stack<int> s1, s2, s3;
    int sum_h1 = 0, sum_h2 = 0, sum_h3 = 0;
    int res = 0;
    for (int i=size(h1)-1; i>=0; i--) {
        s1.push(h1[i]);
        sum_h1 += h1[i];
    }
    for (int i=size(h2)-1; i>=0; i--) {
        s2.push(h2[i]);
        sum_h2 += h2[i];
    }
    for (int i=size(h3)-1; i>=0; i--) {
        s3.push(h3[i]);
        sum_h3 += h3[i];
    }
    res = min(sum_h1, min(sum_h2, sum_h3));
    while (sum_h1 != sum_h2 or sum_h2 != sum_h3) {
        while (sum_h1 > res) {
            sum_h1 -= s1.top();
            s1.pop();
        }
        res = min(sum_h1, min(sum_h2, sum_h3));
        while (sum_h2 > res) {
            sum_h2 -= s2.top();
            s2.pop();
        }
        res = min(sum_h1, min(sum_h2, sum_h3));
        while (sum_h3 > res) {
            sum_h3 -= s3.top();
            s3.pop();
        }
        res = min(sum_h1, min(sum_h2, sum_h3));
    }
    return res;
}
```

</details>

## Queue using Two Stacks
Problem Link: https://hackerrank.com/challenges/queue-using-two-stacks/problem

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def QueueTwoStacks(queries):
    out_stk, in_stk = [], []
    for query in queries:
        val = list(map(int, query.split()))
        if val[0] == 1:
            in_stk.append(val[1])
        elif val[0] == 2:
            if not out_stk:
                while in_stk:
                    out_stk.append(in_stk[-1])
                    in_stk.pop()
            out_stk.pop()
        else:
            print(out_stk[-1] if out_stk else in_stk[0])
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
void QueueTwoStacks(vector<vector<int>> queries) {
    vector<int> out_stk, in_stk;
    for (auto val : queries) {
        if (val[0] == 1)
            in_stk.push_back(val[1]);
        else if (val[0] == 2) {
            if (out_stk.empty()) {
                while (not in_stk.empty()) {
                    out_stk.push_back(in_stk.back());
                    in_stk.pop_back();
                }
            }
            out_stk.pop_back();
        }
        else {
            cout << (not out_stk.empty()? out_stk.back() : in_stk.front()) << '\n';
        }
    }
}
```

</details>

## Balanced Brackets
Problem Link: https://hackerrank.com/challenges/balanced-brackets/problem

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def isBalanced(s):
    if len(s) % 2:
        return "NO"
    open_brackets = "([{"
    stk = []
    match = {'(': ')', '[': ']', '{': '}'};
    for i in s:
        if i in open_brackets:
            stk.append(i)
        else:
            if not stk or i != match[stk[-1]]:
                return "NO"
            stk.pop()
    return "YES" if not stk else "NO"
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
string isBalanced(string s) {
    if (size(s) % 2)
        return "NO";
    string open_brackets = "([{";
    stack<char> stk;
    map<char, char> match = {{'(', ')'}, {'[', ']'}, {'{', '}'}};
    for (char i : s) {
        if (open_brackets.find(i) != string::npos) {
            stk.push(i);
        }
        else {
            if (stk.empty() or i != match[stk.top()])
                return "NO";
            stk.pop();
        }
    }
    return stk.empty()? "YES": "NO";
}
```

</details>

## Castle on the Grid
Problem Link: https://hackerrank.com/challenges/castle-on-the-grid/problem

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def minimumMoves(grid, startX, startY, goalX, goalY):
    def isOpen(grid, x, y):
        return 0 <= x < len(grid) and 0 <= y < len(grid) and grid[x][y] == '.'

    if startX == goalX and startY == goalY:
        return 0
    n = len(grid)
    moves = [[-1 for _ in range(n)] for _ in range(n)]
    moves[startX][startY] = 0
    q = [(startX, startY)]
    dx = [0, 0, 1, -1]
    dy = [1, -1, 0, 0]
    while q:
        head = q[0]
        q.pop(0)
        for i in range(4):
            nextX, nextY = head[0], head[1]
            while isOpen(grid, nextX + dx[i], nextY + dy[i]):
                nextX += dx[i]
                nextY += dy[i]
                if nextX == goalX and nextY == goalY:
                    return moves[head[0]][head[1]] + 1
                if moves[nextX][nextY] == -1:
                    moves[nextX][nextY] = moves[head[0]][head[1]] + 1
                    q.append((nextX, nextY))
    return 0
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
bool isOpen(vector<string> grid, int x, int y) {
    return 0 <= x and x < size(grid) and 0 <= y and y < size(grid) and grid[x][y] == '.';
}

int minimumMoves(vector<string> grid, int startX, int startY, int goalX, int goalY) {
    if (startX == goalX and startY == goalY)
        return 0;
    int n = size(grid);
    vector<vector<int>> moves(n, vector<int>(n, -1));
    moves[startX][startY] = 0;
    vector<pair<int, int>> q = {{startX, startY}};
    int dx[4] = {0, 0, 1, -1};
    int dy[4] = {1, -1, 0, 0};
    while (size(q) > 0) {
        auto head = q.front();
        q.erase(q.begin());
        for (int i=0; i<4; i++) {
            int nextX = head.first, nextY = head.second;
            while (isOpen(grid, nextX + dx[i], nextY + dy[i])) {
                nextX += dx[i];
                nextY += dy[i];
                if (nextX == goalX and nextY == goalY)
                    return moves[head.first][head.second] + 1;
                if (moves[nextX][nextY] == -1) {
                    moves[nextX][nextY] = moves[head.first][head.second] + 1;
                    q.push_back({nextX, nextY});
                }
            }
        }
    }
    return 0;
}
```

</details>

## Down to Zero II
Problem Link: https://hackerrank.com/challenges/down-to-zero-ii/problem

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
N = int(2e6)+3
seive = [0] * N

def constract_seive():
    seive[0], seive[1] = 0, 1
    for i in range(1, N):
        if seive[i] == 0 or seive[i] > seive[i-1] + 1:
            seive[i] = seive[i-1] + 1
        j = 0
        while j < i * i and j + i < N:
            if seive[j + i] == 0 or seive[j + i] > seive[i] + 1:
                seive[j + i] = seive[i] + 1
            j += i

def downToZero(n):
    return seive[n]
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
const int N = 2e6+3;
int seive[N];

void constract_seive() {
    seive[0] = 0, seive[1] = 1;
    for (long long i=1; i<N; i++) {
        if (seive[i] == 0 or seive[i] > seive[i-1] + 1)
            seive[i] = seive[i-1] + 1;
        long long j = 0;
        while (j < i * i and j + i < N) {
            if (seive[j + i] == 0 or seive[j + i] > seive[i] + 1) {
                seive[j + i] = seive[i] + 1;
            }
            j += i;
        }
    }
}

int downToZero(int n) {
    return seive[n];
}
```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.jpg"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.jpg"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

