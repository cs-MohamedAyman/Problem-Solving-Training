<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="80" src="/logos/hackerrank.png"></img></a>

# HackerRank OJ - Algorithms Basics <br> Math Fundamentals II `15 problems`

## Sherlock and Divisors
Problem Link: https://www.hackerrank.com/challenges/sherlock-and-divisors/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def divisors(n):
    i, res = 1, 0
    while i * i <= n:
        if n % i == 0:
            if i % 2 == 0:
                res += 1
            if (n // i) % 2 == 0 and i != n // i:
                res += 1
        i += 1
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int divisors(int n) {
    int i = 1, res = 0;
    while (i * i <= n) {
        if (n % i == 0) {
            if (i % 2 == 0)
                res ++;
            if ((n / i) % 2 == 0 and i != n / i)
                res ++;
        }
        i ++;
    }
    return res;
}
```

</details>

## Halloween party
Problem Link: https://www.hackerrank.com/challenges/halloween-party/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def halloweenParty(k):
    h = k // 2
    v = k - h
    return h * v
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
long halloweenParty(int k) {
    int h = k / 2;
    int v = k - h;
    return 1LL * h * v;
}
```

</details>

## Filling Jars
Problem Link: https://www.hackerrank.com/challenges/filling-jars/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def solve(n, operations):
    res = 0
    for a, b, k in operations:
        res += (b - a + 1) * k
    return res // n
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
long solve(int n, vector<vector<int>> operations) {
    long res = 0;
    for (auto &it : operations)
        res += 1LL * (it[1] - it[0] + 1) * it[2];
    return res / n;
}
```

</details>

## Sumar and the Floating Rocks
Problem Link: https://www.hackerrank.com/challenges/harry-potter-and-the-floating-rocks/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def solve(x1, y1, x2, y2):
    return math.gcd(abs(x2 - x1), abs(y2 - y1)) - 1
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int solve(int x1, int y1, int x2, int y2) {
    return gcd(abs(x2 - x1), abs(y2 - y1)) - 1;
}
```

</details>

## Russian Peasant Exponentiation
Problem Link: https://www.hackerrank.com/challenges/russian-peasant-exponentiation/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def mul_mod(a, b, c, d, m):
    e = (((a%m) * (c%m)) % m - ((b%m)*(d%m)) % m + m) % m
    f = (((a%m) * (d%m)) % m + ((b%m)*(c%m)) % m) % m
    return e, f

def solve(a, b, k, m):
    a %= m
    b %= m
    res1, res2 = 1, 0
    while k:
        if k % 2 == 1:
            res1, res2 = mul_mod(res1, res2, a, b, m)
        a, b = mul_mod(a, b, a, b, m)
        k //= 2
    return res1, res2
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
void mul_mod(long a, long b, long c, long d, long &e, long &f, int m) {
    e = (((a%m) * (c%m)) % m - ((b%m)*(d%m)) % m + m) % m;
    f = (((a%m) * (d%m)) % m + ((b%m)*(c%m)) % m) % m;
}
vector<long> solve(long a, long b, long k, int m) {
    a %= m;
    b %= m;
    long res1 = 1, res2 = 0;
    while (k) {
        if (k % 2 == 1)
            mul_mod(res1, res2, a, b, res1, res2, m);
        mul_mod(a, b, a, b, a, b, m);
        k /= 2LL;
    }
    return {res1, res2};
}
```

</details>

## Most Distant
Problem Link: https://www.hackerrank.com/challenges/most-distant/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def solve(coordinates):
    max_x, min_x, max_y, min_y = -1e9, 1e9, -1e9, 1e9
    for x, y in coordinates:
        max_x = max(max_x, x)
        min_x = min(min_x, x)
        max_y = max(max_y, y)
        min_y = min(min_y, y)
    res = max(max_x - min_x, max_y - min_y)
    res = max(res, (max_x*max_x + max_y*max_y) ** .5)
    res = max(res, (max_x*max_x + min_y*min_y) ** .5)
    res = max(res, (min_x*min_x + max_y*max_y) ** .5)
    res = max(res, (min_x*min_x + min_y*min_y) ** .5)
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>

## Possible Path
Problem Link: https://www.hackerrank.com/challenges/possible-path/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def solve(a, b, x, y):
    return 'YES' if math.gcd(a, b) == math.gcd(x, y) else 'NO'
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
string solve(long a, long b, long x, long y) {
    return gcd(a, b) == gcd(x, y)? "YES" : "NO";
}
```

</details>

## Summing the N series
Problem Link: https://www.hackerrank.com/challenges/summing-the-n-series/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
MOD = int(1e9+7)

def summingSeries(n):
    return ((n % MOD) * (n % MOD)) % MOD
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int MOD = 1e9+7;

int summingSeries(long n) {
    return ((n % MOD) * (n % MOD)) % MOD;
}
```

</details>

## Diwali Lights
Problem Link: https://www.hackerrank.com/challenges/diwali-lights/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
MOD = int(1e5)

def fast_pow(b, e):
    res = 1
    while e:
        if e % 2 == 1:
            res = res * b % MOD
        b = b * b % MOD
        e //= 2
    return res

def lights(n):
    res = fast_pow(2, n)
    return (res - 1 + MOD) % MOD
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int MOD = 1e5;

int fast_pow(int b, int e) {
    int res = 1;
    while (e) {
        if (e % 2 == 1)
            res = 1LL * res * b % MOD;
        b = 1LL * b * b % MOD;
        e /= 2;
    }
    return res;
}
long lights(int n) {
    long res = fast_pow(2, n);
    return (res - 1 + MOD) % MOD;
}
```

</details>

## Special Multiple
Problem Link: https://www.hackerrank.com/challenges/special-multiple/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def solve(n):
    if n == 1:
        return '9'
    i = 1
    res = 1
    while res % n != 0:
        res, temp, j = 0, 9, i
        while j:
            if j % 2 == 1:
                res += temp
            temp *= 10
            j //= 2
        i += 1
    return str(res)
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
string solve(int n) {
    if (n == 1)
        return "9";
    int i = 1, j = 1;
    long res = 1, temp = 9;
    while (res % n != 0) {
        res = 0, temp = 9, j = i;
        while (j) {
            if (j % 2 == 1)
                res += temp;
            temp *= 10;
            j /= 2;
        }
        i ++;
    }
    return to_string(res);
}
```

</details>

## Sherlock and Permutations
Problem Link: https://www.hackerrank.com/challenges/sherlock-and-permutations/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
MOD = int(1e9+7)
N = int(2e3+3)
fact = [0] * N

def fast_pow(b, e):
    res = 1
    while e:
        if e % 2 == 1:
            res = res * b % MOD
        b = b * b % MOD
        e //= 2
    return res

def solve(n, m):
    return fact[n+m-1] * fast_pow(fact[m-1] * fact[n] % MOD, MOD-2) % MOD

def build_prerequisite():
    fact[0] = 1
    for i in range(1, N):
        fact[i] = fact[i-1] * i % MOD
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int MOD = 1e9+7;
const int N = 2e3+3;
int fact[N];

int fast_pow(int b, int e) {
    int res = 1;
    while (e) {
        if (e % 2 == 1)
            res = 1LL * res * b % MOD;
        b = 1LL * b * b % MOD;
        e /= 2;
    }
    return res;
}
int solve(int n, int m) {
    return 1LL * fact[n+m-1] * fast_pow(1LL * fact[m-1] * fact[n] % MOD, MOD-2) % MOD;
}
void build_prerequisite() {
    fact[0] = 1;
    for (int i = 1; i < N; i++)
        fact[i] = 1LL * fact[i-1] * i % MOD;
}
```

</details>

## Even Odd Query
Problem Link: https://www.hackerrank.com/challenges/even-odd-query/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def solve(arr, queries):
    res = []
    for x, y in queries:
        if x < len(arr) and arr[x] == 0 and x != y:
            res.append('Odd')
        else:
            res.append('Even' if arr[x-1] % 2 == 0 else 'Odd')
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
vector<string> solve(vector<int> arr, vector<vector<int>> queries) {
    vector<string> res;
    for (auto &it : queries) {
        if (it[0] < size(arr) and arr[it[0]] == 0 and it[0] != it[1])
            res.push_back("Odd");
        else
            res.push_back(arr[it[0]-1] % 2 == 0? "Even" : "Odd");
    }
    return res;
}
```

</details>

## Matrix Tracing
Problem Link: https://www.hackerrank.com/challenges/matrix-tracing/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
MOD = int(1e9+7)
N = int(2e6+3)
fact = [0] * N

def fast_pow(b, e):
    res = 1
    while e:
        if e % 2 == 1:
            res = res * b % MOD
        b = b * b % MOD
        e //= 2
    return res

def solve(n, m):
    return fact[n+m-2] * fast_pow(fact[n-1] * fact[m-1] % MOD, MOD-2) % MOD

def build_prerequisite():
    fact[0] = 1
    for i in range(1, N):
        fact[i] = fact[i-1] * i % MOD
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int MOD = 1e9+7;
const int N = 2e6+3;
int fact[N];

int fast_pow(int b, int e) {
    int res = 1;
    while (e) {
        if (e % 2 == 1)
            res = 1LL * res * b % MOD;
        b = 1LL * b * b % MOD;
        e /= 2;
    }
    return res;
}
int solve(int n, int m) {
    return 1LL * fact[n+m-2] * fast_pow(1LL * fact[n-1] * fact[m-1] % MOD, MOD-2) % MOD;
}
void build_prerequisite() {
    fact[0] = 1;
    for (int i = 1; i < N; i++)
        fact[i] = 1LL * fact[i-1] * i % MOD;
}
```

</details>

## Byteland Itinerary
Problem Link: https://www.hackerrank.com/challenges/byteland-itinerary/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>
