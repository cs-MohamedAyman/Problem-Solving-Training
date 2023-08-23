<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="80" src="/logos/hackerrank.png"></img></a>

# HackerRank OJ - Algorithms Basics <br> Implementation II `15 problems`

## Beautiful Days at the Movies
Problem Link: https://www.hackerrank.com/challenges/beautiful-days-at-the-movies/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def reverse(x):
    res = 0
    while x:
        res = res * 10 + x % 10
        x //= 10
    return res

def beautifulDays(i, j, k):
    res = 0
    while i <= j:
        diff = abs(i - reverse(i))
        if diff % k == 0:
            res += 1
        i += 1
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int reverse(int x) {
    int res = 0;
    while (x) {
        res = res * 10 + x % 10;
        x /= 10;
    }
    return res;
}
int beautifulDays(int i, int j, int k) {
    int res = 0;
    while (i <= j) {
        int diff = abs(i - reverse(i));
        if (diff % k == 0)
            res ++;
        i ++;
    }
    return res;
}
```

</details>

## Viral Advertising
Problem Link: https://www.hackerrank.com/challenges/strange-advertising/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def viralAdvertising(n):
    curr, res = 5, 0
    for i in range(1, n+1):
        res += curr // 2
        curr = curr // 2 * 3
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int viralAdvertising(int n) {
    int curr = 5, res = 0;
    for (int i=1; i<n+1; i++) {
        res += curr / 2;
        curr = curr / 2 * 3;
    }
    return res;
}
```

</details>

## Save the Prisoner!
Problem Link: https://www.hackerrank.com/challenges/save-the-prisoner/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def saveThePrisoner(n, m, s):
    res = (s + m - 1) % n
    return res if res != 0 else n
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int saveThePrisoner(int n, int m, int s) {
    int res = (s + m - 1) % n;
    return (res != 0? res : n);
}
```

</details>

## Circular Array Rotation
Problem Link: https://www.hackerrank.com/challenges/circular-array-rotation/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def circularArrayRotation(a, k, queries):
    x = k % len(a)
    a = a[-x:] + a[:-x]
    res = []
    for i in queries:
        res.append(a[i])
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
vector<int> circularArrayRotation(vector<int> a, int k, vector<int> queries) {
    int x = k % size(a);
    vector<int> t(a.begin(), a.end()-x);
    t.insert(t.begin(), a.end()-x, a.end());
    vector<int> res;
    for (auto &i : queries)
        res.push_back(t[i]);
    return res;
}
```

</details>

## Sequence Equation
Problem Link: https://www.hackerrank.com/challenges/permutation-equation/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def permutationEquation(p):
    res = [0] * len(p)
    for i in range(len(p)):
        for j in range(len(p)):
            if i+1 == p[p[j]-1]:
                res[i] = j+1
                break
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
vector<int> permutationEquation(vector<int> p) {
    vector<int> res(size(p));
    for (int i=0; i<size(p); i++) {
        for (int j=0; j<size(p); j++) {
            if (i+1 == p[p[j]-1]) {
                res[i] = j+1;
                break;
            }
        }
    }
    return res;
}
```

</details>

## Jumping on the Clouds: Revisited
Problem Link: https://www.hackerrank.com/challenges/jumping-on-the-clouds-revisited/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def jumpingOnClouds(c, k):
    curr = k % len(c)
    res = 99 - c[curr] * 2
    while curr:
        curr = (curr + k) % len(c)
        res -= 1 + c[curr] * 2
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int jumpingOnClouds(vector<int> c, int k) {
    int curr = k % size(c);
    int res = 99 - c[curr] * 2;
    while (curr) {
        curr = (curr + k) % size(c);
        res -= 1 + c[curr] * 2;
    }
    return res;
}
```

</details>

## Find Digits
Problem Link: https://www.hackerrank.com/challenges/find-digits/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def findDigits(n):
    res, m = 0, n
    while m:
        d = m % 10
        m //= 10
        if d != 0 and n % d == 0:
            res += 1
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int findDigits(int n) {
    int res = 0, m = n;
    while (m) {
        int d = m % 10;
        m /= 10;
        if (d != 0 and n % d == 0)
            res ++;
    }
    return res;
}
```

</details>

## Append and Delete
Problem Link: https://www.hackerrank.com/challenges/append-and-delete/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def appendAndDelete(s, t, k):
    i = 0
    while i < min(len(s), len(t)) and s[i] == t[i]:
        i += 1
    x = len(s) + len(t) - (2 * i)
    if x <= k and ((k - x) % 2 == 0 or (len(s) + len(t)) <= k):
        return "Yes"
    else:
        return "No"
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
string appendAndDelete(string s, string t, int k) {
    int i = 0;
    while (i < min(size(s), size(t)) and s[i] == t[i])
        i ++;
    int x = size(s) + size(t) - (2 * i);
    if (x <= k and ((k - x) % 2 == 0 or (size(s) + size(t)) <= k))
        return "Yes";
    else
        return "No";
}
```

</details>

## Sherlock and Squares
Problem Link: https://www.hackerrank.com/challenges/sherlock-and-squares/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def squares(a, b):
    res = int(b ** .5) - int((a-1) ** .5)
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int squares(int a, int b) {
    int res = int(sqrt(b)) - int(sqrt(a-1));
    return res;
}
```

</details>

## Library Fine
Problem Link: https://www.hackerrank.com/challenges/library-fine/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def libraryFine(d1, m1, y1, d2, m2, y2):
    if (y1 < y2) or (y1 == y2 and m1 < m2) or (y1 == y2 and m1 == m2 and d1 <= d2):
        return 0
    elif y1 == y2 and m1 == m2 and d1 > d2:
        return 15 * (d1 - d2)
    elif y1 == y2 and m1 > m2:
        return 500 * (m1 - m2)
    else:
        return 10000
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int libraryFine(int d1, int m1, int y1, int d2, int m2, int y2) {
    if ((y1 < y2) or (y1 == y2 and m1 < m2) or (y1 == y2 and m1 == m2 and d1 <= d2))
        return 0;
    else if (y1 == y2 and m1 == m2 and d1 > d2)
        return 15 * (d1 - d2);
    else if (y1 == y2 and m1 > m2)
        return 500 * (m1 - m2);
    else
        return 10000;
}
```

</details>

## Cut the sticks
Problem Link: https://www.hackerrank.com/challenges/cut-the-sticks/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def cutTheSticks(arr):
    d = {}
    for i in arr:
        d[i] = d.get(i, 0) + 1
    d = sorted(list(d.items()))
    res = [len(arr)]
    for _, n in d[:-1]:
        res.append(res[-1] - n)
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
vector<int> cutTheSticks(vector<int> arr) {
    map<int, int> d;
    for (auto &i : arr)
        d[i] ++;
    vector<int> res = {int(size(arr))};
    d.erase(--d.end());
    for (auto &[_, n] : d)
        res.push_back(res[size(res)-1] - n);
    return res;
}
```

</details>

## Repeated String
Problem Link: https://www.hackerrank.com/challenges/repeated-string/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def repeatedString(s, n):
    cnt = 0
    for i in range(len(s)):
        if s[i] == 'a':
            cnt += 1
    res = (n // len(s)) * cnt
    for i in range(n % len(s)):
        if s[i] == 'a':
            res += 1
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
long repeatedString(string s, long n) {
    int cnt = 0;
    for (int i = 0; i < size(s); i++) {
        if (s[i] == 'a')
            cnt ++;
    }
    long res = 1LL * (n / size(s)) * cnt;
    for (int i = 0; i < n % size(s); i++) {
        if (s[i] == 'a')
            res ++;
    }
    return res;
}
```

</details>

## Jumping on the Clouds
Problem Link: https://www.hackerrank.com/challenges/jumping-on-the-clouds/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def jumpingOnClouds(c):
    res, i = 0, 0
    while i < len(c)-1:
        if i+2 < len(c) and c[i+2] == 0:
            i += 1
        i += 1
        res += 1
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int jumpingOnClouds(vector<int> c) {
    int res = 0, i = 0;
    while (i < size(c)-1) {
        if (i+2 < size(c) and c[i+2] == 0)
            i ++;
        i ++;
        res ++;
    }
    return res;
}
```

</details>

## Equalize the Array
Problem Link: https://www.hackerrank.com/challenges/equality-in-a-array/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def equalizeArray(arr):
    cnt = {}
    for i in arr:
        cnt[i] = cnt.get(i, 0) + 1
    most_freq = sorted(list(cnt.items()), key=lambda x: x[1])[-1][0]
    res = 0
    for i in arr:
        if i != most_freq:
            res += 1
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int equalizeArray(vector<int> arr) {
    map<int, int> cnt;
    for (auto &i : arr)
        cnt[i] ++;
    vector<pair<int, int>> v(cnt.begin(), cnt.end());
    auto comp = [](const pair<int, int> &x, const pair<int, int> &y) {
        return x.second < y.second;
    };
    sort(v.begin(), v.end(), comp);
    int most_freq = v.back().first;
    int res = 0;
    for (auto &i : arr) {
        if (i != most_freq)
            res ++;
    }
    return res;
}
```

</details>

## ACM ICPC Team
Problem Link: https://www.hackerrank.com/challenges/acm-icpc-team/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def acmTeam(topic):
    ele, cnt = 0, 0
    n, m = len(topic), len(topic[0])
    for i in range(n-1):
        for j in range(i+1, n):
            x = 0
            for k in range(m):
                x += int(topic[i][k] == '1' or topic[j][k] == '1')
            if ele < x:
                ele = x
                cnt = 1
            elif x == ele:
                cnt += 1
    return ele, cnt
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
vector<int> acmTeam(vector<string> topic) {
    int ele = 0, cnt = 0;
    int n = size(topic), m = size(topic[0]);
    for (int i=0; i<n-1; i++) {
        for (int j=i+1; j<n; j++) {
            int x = 0;
            for (int k=0; k<m; k++)
                x += int(topic[i][k] == '1' or topic[j][k] == '1');
            if (ele < x) {
                ele = x;
                cnt = 1;
            }
            else if (x == ele)
                cnt ++;
        }
    }
    return {ele, cnt};
}
```

</details>

## Taum and B'day
Problem Link: https://www.hackerrank.com/challenges/taum-and-bday/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def taumBday(b, w, bc, wc, z):
    i = min(bc, wc + z)
    j = min(wc, bc + z)
    return (b * i) + (w * j)
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
long taumBday(int b, int w, int bc, int wc, int z) {
    long i = min(bc, wc + z);
    long j = min(wc, bc + z);
    return 1LL * (b * i) + (w * j);
}
```

</details>
