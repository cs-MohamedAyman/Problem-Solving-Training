<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="80" src="/logos/hackerrank.png"></img></a>

# HackerRank OJ - Data Structures <br> Advanced `20 problems`

## Kindergarten Adventures
Problem Link: https://www.hackerrank.com/challenges/kindergarten-adventures/problem

<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def solve(t):
    n = len(t)
    arr = [0] * (n + 1)
    i = 0
    while i < n:
        r1 = max(0, i+1-t[i])
        r2 = min(max(0, n-t[i])+i+1, n)
        arr[0] +=  1
        arr[i+1] += 1
        arr[r1] -= 1
        arr[r2] -= 1
        i += 1
    for i in range(n):
        arr[i+1] += arr[i]
    return arr.index(max(arr))+1
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int solve(vector<int> &t) {
    int n = size(t);
    vector<int> arr(n+1, 0);
    int i = 0;
    while (i < n) {
        int r1 = max(0, i+1-t[i]);
        int r2 = min(max(0, n-t[i])+i+1, n);
        arr[0] ++;
        arr[i+1] ++;
        arr[r1] --;
        arr[r2] --;
        i ++;
    }
    for (int i=0; i<n; i++)
        arr[i+1] += arr[i];
    int max_arr = *max_element(arr.begin(), arr.end());
    return find(arr.begin(), arr.end(), max_arr)-arr.begin()+1;
}
```

</details>

## Mr. X and His Shots
Problem Link: https://www.hackerrank.com/challenges/x-and-his-shots/problem

<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>

## Jim and the Skyscrapers
Problem Link: https://www.hackerrank.com/challenges/jim-and-the-skyscrapers/problem

<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
N = int(3e5+3)
a = [0] * N
b = [0] * N

def printNGE(v):
    stk = []
    stk.append(0)
    for i in range(1, len(v)):
        while stk and v[stk[-1]] <= v[i]:
            a[stk[-1]] = i
            stk.pop()
        stk.append(i)
    while stk:
        a[stk[-1]] = -1
        stk.pop()

def solve(arr):
    printNGE(arr)
    res = 0
    for i in range(len(arr)):
        if arr[i] == arr[a[i]]:
            b[a[i]] = b[i] + 1
    for i in range(len(arr)):
        res += b[i]
    return 2 * res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
const int N = 3e5+3;
int a[N], b[N];

void printNGE(vector<int> &v) {
    stack<int> stk;
    stk.push(0);
    for (int i=1; i<size(v); i++) {
        while (!stk.empty() and v[stk.top()] <= v[i]) {
            a[stk.top()] = i;
            stk.pop();
        }
        stk.push(i);
    }
    while (!stk.empty()) {
        a[stk.top()] = -1;
        stk.pop();
    }
}
long solve(vector<int> &arr) {
    printNGE(arr);
    long res = 0;
    for (int i=0; i<size(arr); i++) {
        if (arr[i] == arr[a[i]])
            b[a[i]] = b[i] + 1;
    }
    for (int i=0; i<size(arr); i++)
        res += b[i];
    return 2LL * res;
}
```

</details>

## Find Maximum Index Product
Problem Link: https://www.hackerrank.com/challenges/find-maximum-index-product/problem

<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def find_direction(arr, direction):
    stk = [1]
    res = []
    for i in range(1, len(arr)-1):
        while stk and arr[stk[-1]-1] <= arr[i]:
            stk.pop()
        if direction:
            temp = stk[-1] if stk else 0
        else:
            temp = len(arr) - stk[-1] + 1 if stk else 0
        res.append(temp)
        stk.append(i+1)
    return res

def solve(arr):
    res = 0
    left = find_direction(arr, True)
    arr = arr[::-1]
    right = find_direction(arr, False)
    right = right[::-1]
    for i in range(len(left)):
        res = max(res, left[i] * right[i])
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
vector<int> find_direction(vector<int> &arr, bool direction) {
    stack<int> stk;
    stk.push(1);
    vector<int> res;
    for (int i=1; i<size(arr)-1; i++) {
        while (!stk.empty() and arr[stk.top()-1] <= arr[i])
            stk.pop();
        int temp;
        if (direction)
            temp = (!stk.empty()? stk.top() : 0);
        else
            temp = (!stk.empty()? size(arr) - stk.top() + 1 : 0);
        res.push_back(temp);
        stk.push(i+1);
    }
    return res;
}
long solve(vector<int> &arr) {
    long res = 0LL;
    vector<int> left = find_direction(arr, true);
    reverse(arr.begin(), arr.end());
    vector<int> right = find_direction(arr, false);
    reverse(right.begin(), right.end());
    for (int i=0; i<size(left); i++)
        res = max(1LL * res, 1LL * left[i] * right[i]);
    return res;
}
```

</details>

## Cube Summation
Problem Link: https://www.hackerrank.com/challenges/cube-summation/problem

<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def cubeSum(n, operations):
    d = {}
    res = []
    for s in operations:
        cmd = s.split()
        if cmd[0] == 'UPDATE':
            x = int(cmd[1]); y = int(cmd[2])
            z = int(cmd[3]); v = int(cmd[4])
            x -= 1; y -= 1; z -= 1
            d[x + n*y + n*n*z] = v
        else:
            total = 0
            x1 = int(cmd[1]); y1 = int(cmd[2]); z1 = int(cmd[3])
            x2 = int(cmd[4]); y2 = int(cmd[5]); z2 = int(cmd[6])
            for k, v in d.items():
                x = k % n
                y = (k//n) % n
                z = k // (n*n)
                x += 1; y += 1; z += 1
                if x1 <= x <= x2 and y1 <= y <= y2 and z1 <= z <= z2:
                    total += v
            res.append(total)
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
vector<string> split(string s, char sep) {
    int i = 0;
    string temp = "";
    vector<string> res;
    while (i < size(s)) {
        if (s[i] != sep)
            temp += s[i];
        else {
            res.push_back(temp);
            temp.clear();
        }
        i++;
    }
    res.push_back(temp);
    return res;
}
vector<long> cubeSum(int n, vector<string> &operations) {
    map<long, int> d;
    vector<long> res;
    for (auto &s : operations) {
        auto cmd = split(s, ' ');
        if (cmd[0] == "UPDATE") {
            int x = stoi(cmd[1]), y = stoi(cmd[2]), 
                z = stoi(cmd[3]), v = stoi(cmd[4]);
            x --; y --; z --;
            d[x + n*y + n*n*z] = v;
        }
        else {
            long total = 0;
            int x1 = stoi(cmd[1]), y1 = stoi(cmd[2]), z1 = stoi(cmd[3]);
            int x2 = stoi(cmd[4]), y2 = stoi(cmd[5]), z2 = stoi(cmd[6]);
            for (auto &[k, v] : d) {
                int x = k % n;
                int y = (k/n) % n;
                int z = k / (n*n);
                x ++; y ++; z ++;
                if (x1 <= x and x <= x2 and 
                    y1 <= y and y <= y2 and 
                    z1 <= z and z <= z2)
                    total += v;
            }
            res.push_back(total);
        }
    }
    return res;
}
```

</details>

## Direct Connections
Problem Link: https://www.hackerrank.com/challenges/direct-connections/problem

<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>

## Palindromic Subsets
Problem Link: https://www.hackerrank.com/challenges/palindromic-subsets/problem

<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>

## Polynomial Division
Problem Link: https://www.hackerrank.com/challenges/polynomial-division/problem

<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>

## Costly Intervals
Problem Link: https://www.hackerrank.com/challenges/costly-intervals/problem

<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>

## The Strange Function
Problem Link: https://www.hackerrank.com/challenges/the-strange-function/problem

<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>

## Lazy White Falcon
Problem Link: https://www.hackerrank.com/challenges/lazy-white-falcon/problem

<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>

## Heavy Light White Falcon
Problem Link: https://www.hackerrank.com/challenges/heavy-light-white-falcon/problem

<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>

## Heavy Light 2 White Falcon
Problem Link: https://www.hackerrank.com/challenges/heavy-light-2-white-falcon/problem

<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>

## Burger Happiness
Problem Link: https://www.hackerrank.com/challenges/burger-happiness/problem

<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>

## Roy and alpha-beta trees
Problem Link: https://www.hackerrank.com/challenges/roy-and-alpha-beta-trees/problem

<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>

## Coloring Tree
Problem Link: https://www.hackerrank.com/challenges/coloring-tree/problem

<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>

## Recalling Early Days GP with Trees
Problem Link: https://www.hackerrank.com/challenges/recalling-early-days-gp-with-trees/problem

<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>

## White Falcon And Tree
Problem Link: https://www.hackerrank.com/challenges/white-falcon-and-tree/problem

<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>

## Jaggu Playing with Balloons
Problem Link: https://www.hackerrank.com/challenges/jagia-playing-with-numbers/problem

<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>

## Two Array Problem
Problem Link: https://www.hackerrank.com/challenges/weird-queries/problem

<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/advanced-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>
