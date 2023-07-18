<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="80" src="/logos/hackerrank.png"></img></a>

# HackerRank OJ - Data Structures <br> Stacks & Queues `10 problems`

## Equal Stacks
Problem Link: https://hackerrank.com/challenges/equal-stacks/problem

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def equalStacks(h1, h2, h3):
    s1, s2, s3 = [], [], []
    sum_h1, sum_h2, sum_h3 = 0, 0, 0
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
            s2.pop()
        res = min(sum_h1, sum_h2, sum_h3)
        while sum_h3 > res:
            sum_h3 -= s3[-1]
            s3.pop()
        res = min(sum_h1, sum_h2, sum_h3)
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
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

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
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
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
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
        else
            cout << (not out_stk.empty()? out_stk.back() : in_stk.front()) << '\n';
    }
}
```

</details>

## Balanced Brackets
Problem Link: https://hackerrank.com/challenges/balanced-brackets/problem

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
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
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
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
        if (open_brackets.find(i) != string::npos)
            stk.push(i);
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

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
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
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
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
        for (int i = 0; i < 4; i++) {
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

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
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
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
const int N = 2e6+3;
int seive[N];

void constract_seive() {
    seive[0] = 0, seive[1] = 1;
    for (long long i = 1; i < N; i++) {
        if (seive[i] == 0 or seive[i] > seive[i-1] + 1)
            seive[i] = seive[i-1] + 1;
        long long j = 0;
        while (j < i * i and j + i < N) {
            if (seive[j + i] == 0 or seive[j + i] > seive[i] + 1)
                seive[j + i] = seive[i] + 1;
            j += i;
        }
    }
}

int downToZero(int n) {
    return seive[n];
}
```

</details>

## Largest Rectangle
Problem Link: https://www.hackerrank.com/challenges/largest-rectangle/problem

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def largestRectangle(h):
    stk = []
    i = 0
    res = 0

    while i < len(h):
        if (not stk) or (h[stk[-1]] <= h[i]):
            stk.append(i)
            i += 1
        else:
            t = stk.pop()
            area = h[t] * ((i - stk[-1] - 1) if stk else i)
            res = max(res, area)

    while stk:
        t = stk.pop()
        area = h[t] * ((i - stk[-1] - 1) if stk else i)
        res = max(res, area)

    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
long largestRectangle(vector<int> h) {
    stack<int> stk;
    int i = 0;
    int res = 0;

    while (i < size(h)) {
        if (stk.empty() or (h[stk.top()] <= h[i])) {
            stk.push(i);
            i ++;
        }
        else {
            int t = stk.top();
            stk.pop();
            int area = h[t] * (!stk.empty()? i - stk.top() - 1 : i);
            res = max(res, area);
        }
    }
    while (!stk.empty()) {
        int t = stk.top();
        stk.pop();
        int area = h[t] * (!stk.empty()? i - stk.top() - 1 : i);
        res = max(res, area);
    }
    return res;
}
```

</details>

## Simple Text Editor
Problem Link: https://www.hackerrank.com/challenges/simple-text-editor/problem

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class TextEditor:
    def __init__(self):
        self.text = []
    def append(self, s):
        self.text.append(self.last() + s)
    def remove(self, n):
        self.text.append(self.last()[:-n])
    def at(self, k):
        return self.last()[k - 1]
    def undo(self):
        self.text.pop()
    def last(self):
        return self.text[-1] if self.text else ''

n = int(input())
t = TextEditor()
queries = list(input().split() for _ in range(n))
res = []
for cmd in queries:
    if cmd[0] == '1':
        t.append(cmd[1])
    elif cmd[0] == '2':
        t.remove(int(cmd[1]))
    elif cmd[0] == '3':
        res.append(t.at(int(cmd[1])))
    elif cmd[0] == '4':
        t.undo()
print('\n'.join(res))
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
struct TextEditor {
    stack<string> text;

    void append(string s) {
        text.push(last() + s);
    }
    void remove(int n) {
        string last_str = last();
        text.push(last_str.substr(0, size(last_str)-n));
    }
    char at(int k) {
        return last()[k - 1];
    }
    void undo() {
        text.pop();
    }
    string last() {
        return (!text.empty()? text.top() : "");
    }
};
int main() {
    int n;
    cin >> n;
    TextEditor t;
    vector<char> res;
    for (int i = 0; i < n; i++) {
        int x;
        cin >> x;
        if (x == 1) {
            string cmd;
            cin >> cmd;
            t.append(cmd);            
        }
        else if (x == 2) {
            int cmd;
            cin >> cmd;
            t.remove(cmd);
        }
        else if (x == 3) {
            int cmd;
            cin >> cmd;
            res.push_back(t.at(cmd));
        }
        else {
            t.undo();
        }
    }
    for (auto &c : res)
        cout << c << '\n';
}
```

</details>

## Waiter
Problem Link: https://www.hackerrank.com/challenges/waiter/problem

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def constract_seive():
    N = int(5e4)+3
    seive = [0] * N
    primes = []
    for i in range(2, N):
        if seive[i] == 1:
            continue
        primes.append(i)
        j = i * i
        while j < N:
            seive[j] = 1
            j += i
    return primes

def waiter(nums, q):
    res, strA, strB = [], [], []
    primes = constract_seive()
    for i in range(q):
        while nums:
            if nums[-1] % primes[i] == 0:
                strB.append(nums[-1])
            else:
                strA.append(nums[-1])
            nums.pop()
        nums = strA[:]
        strA.clear()
        while strB:
            res.append(strB[-1])
            strB.pop()
    while nums:
        res.append(nums[-1])
        nums.pop()
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
vector<int> constract_seive() {
    int N = int(5e4)+3;
    vector<bool> seive(N, 0);
    vector<int> primes;
    for (int i = 2; i < N; i++) {
        if (seive[i] == 1)
            continue;
        primes.push_back(i);
        long long j = 1LL * i * i;
        while (j < N) {
            seive[j] = 1;
            j += i;
        }
    }
    return primes;
}
vector<int> waiter(vector<int> nums, int q) {
    vector<int> res, strA, strB;   
    vector<int> primes = constract_seive();
    for (int i = 0; i < q; i++) {
        while (!nums.empty()) {
            if (nums.back() % primes[i] == 0)
                strB.push_back(nums.back());
            else
                strA.push_back(nums.back());    
            nums.pop_back();
        }
        nums = strA;
        strA.clear();
        while (!strB.empty()) {
            res.push_back(strB.back());
            strB.pop_back();
        }
    }
    while (!nums.empty()) {
        res.push_back(nums.back());
        nums.pop_back();
    }
    return res;
}
```

</details>

## Truck Tour
Problem Link: https://www.hackerrank.com/challenges/truck-tour/problem

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def truckTour(pumps):
    curr_pet, curr_pos = 0, 0
    for i in range(len(pumps)):
        petrol, distance = pumps[i][0], pumps[i][1]
        curr_pet += petrol
        if curr_pet > distance:
            curr_pet -= distance
        else:
            curr_pet, curr_pos = 0, i
    return curr_pos + 1
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int truckTour(vector<vector<int>> pumps) {
    int curr_pet = 0, curr_pos = 0;
    for (int i = 0; i < size(pumps); i++) {
        int petrol = pumps[i][0], distance = pumps[i][1];
        curr_pet += petrol;
        if (curr_pet > distance)
            curr_pet -= distance;
        else
            curr_pet = 0, curr_pos = i;
    }
    return curr_pos + 1;
}
```

</details>

## Queries with Fixed Length
Problem Link: https://www.hackerrank.com/challenges/queries-with-fixed-length/problem

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def solve(arr, queries):
    dq = []
    res = []
    for d in queries:
        dq.clear()
        curr_min = 2e9
        for i in range(len(arr)):
            while dq and arr[dq[-1]] < arr[i]:
                dq.pop()
            dq.append(i)
            while dq and dq[0] <= i - d:
                dq.pop(0)
            if i >= d - 1:
                curr_min = min(curr_min, arr[dq[0]])
        res.append(curr_min)
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
vector<int> solve(vector<int> arr, vector<int> queries) {
    deque<int> dq;
    vector<int> res;
    for (int &d : queries) {
        dq.clear();
        int curr_min = 2e9;
        for (int i = 0; i < size(arr); i++) {
            while (size(dq) and arr[dq.back()] < arr[i])
                dq.pop_back();
            dq.push_back(i);
            while (size(dq) and dq.front() <= i - d)
                dq.pop_front();
            if (i >= d - 1)
                curr_min = min(curr_min, arr[dq.front()]);
        }
        res.push_back(curr_min);
    }
    return res;
}
```

</details>

## Poisonous Plants
Problem Link: https://www.hackerrank.com/challenges/poisonous-plants/problem

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def poisonousPlants(p):
    stk = []
    max_height, max_diff = 0, 0
    for i in range(len(p)-1, -1, -1):
        while stk and p[i] < stk[-1]:
            stk.pop()
        max_diff = max(max_diff, max_height - len(stk))
        stk.append(p[i])
        max_height = max(max_height, len(stk))
    return max_diff
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int poisonousPlants(vector<int> p) {
    vector<int> stk;
    int max_height = 0, max_diff = 0;
    for (int i = size(p)-1; i > -1; i--) {
        while (size(stk) > 0 and p[i] < stk.back())
            stk.pop_back();
        max_diff = max(max_diff, max_height - int(size(stk)));
        stk.push_back(p[i]);
        max_height = max(max_height, int(size(stk)));
    }
    return max_diff;
}
```

</details>

## AND xor OR
Problem Link: https://www.hackerrank.com/challenges/and-xor-or/problem

<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def andXorOr(a):
    res = 0
    stk = []
    for i in a:
        while stk:
            res = max(res, i ^ stk[-1])
            if i < stk[-1]:
                stk.pop()
            else:
                break
        stk.append(i)
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int andXorOr(vector<int> a) {
    int res = 0;
    stack<int> stk;
    for (int &i : a) {
        while (size(stk)) {
            res = max(res, i ^ stk.top());
            if (i < stk.top())
                stk.pop();
            else
                break;
        }
        stk.push(i);
    }
    return res;
}
```

</details>
