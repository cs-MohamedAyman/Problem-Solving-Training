<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="80" src="/logos/hackerrank.png"></img></a>

# HackerRank OJ - Data Structures <br> Bit Manipulation `15 problems`

## Lonely Integer
Problem Link: https://hackerrank.com/challenges/lonely-integer/problem

<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def lonelyinteger(a):
    res = 0
    for i in a:
        res ^= i
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int lonelyinteger(vector<int> &a) {
    int res = 0;
    for (auto &i : a)
        res ^= i;
    return res;
}
```

</details>

## Maximizing XOR
Problem Link: https://hackerrank.com/challenges/maximizing-xor/problem

<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def maximizingXor(l, r):
    res = 0
    for i in range(l, r+1):
        for j in range(i, r+1):
            res = max(res, j ^ i)
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int maximizingXor(int l, int r) {
    int res = 0;
    for (int i = l; i < r+1; i++)
        for (int j = i; j < r+1; j++)
            res = max(res, j ^ i);
    return res;
}
```

</details>

## Sum vs XOR
Problem Link: https://hackerrank.com/challenges/sum-vs-xor/problem

<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def sumXor(n):
    res = 0
    while n:
        res += 1 - (n % 2)
        n >>= 1
    return 1 << res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
long sumXor(long n) {
    int res = 0;
    while (n) {
        res += 1 - (n % 2);
        n >>= 1;
    }
    return 1LL << res;
}
```

</details>

## Flipping bits
Problem Link: https://hackerrank.com/challenges/flipping-bits/problem

<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def flippingBits(n):
    return (1 << 32) - 1 - n
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
long flippingBits(long n) {
    return (1LL << 32) - 1 - n;
}
```

</details>

## Counter game
Problem Link: https://hackerrank.com/challenges/counter-game/problem

<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def counterGame(n):
    res = 0
    while n != 1:
        cnt = 0
        temp = n
        while temp:
            temp >>= 1
            cnt +=1
        a = 1 << (cnt - 1)
        if n == a:
            n >>= 1
        else:
            n -= a
        res += 1
    return ('Richard' if res % 2 == 0 else 'Louise')
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
string counterGame(long n) {
    int res = 0;
    while (n != 1) {
        int cnt = 0;
        long temp = n;
        while (temp) {
            temp >>= 1;
            cnt ++;
        }
        long a = 1LL << (cnt - 1);
        if (n == a)
            n >>= 1;
        else
            n -= a;
        res ++;
    }
    return (res % 2 == 0 ? "Richard" : "Louise");
}
```

</details>

## Xor-sequence
Problem Link: https://hackerrank.com/challenges/xor-se/problem

<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def clac_xor(x):
    y = (x >> 2) << 2
    res = 0
    for i in range(y, x+1):
        res ^= i
    return res

def get(x):
    if x == 0:
        return 0
    k = (x + 1) >> 1
    if x % 2:
        return (clac_xor(k-1) * 2) ^ (k & 1)
    else:
        return 2 * clac_xor(k)

def xorSequence(l, r):
    return get(r) ^ get(l-1)

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
long clac_xor(long x) {
    long y = (x >> 2) << 2;
    long res = 0;
    for (long i=y; i<x+1; i++)
        res ^= i;
    return res;
}
long get(long x) {
    if (x == 0)
        return 0;
    long k = (x + 1) >> 1;
    if (x % 2)
        return (clac_xor(k-1) * 2LL) ^ (k & 1LL);
    else
        return 2LL * clac_xor(k);
}
long xorSequence(long l, long r) {
    return get(r) ^ get(l-1);
}
```

</details>

## The Great XOR
Problem Link: https://hackerrank.com/challenges/the-great-xor/problem

<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def theGreatXor(x):
    res = 0
    mask = 1
    while mask < x:
        if (mask & x) == 0:
            res += mask
        mask <<= 1
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
long theGreatXor(long x) {
    long res = 0;
    long mask = 1;
    while (mask < x) {
        if ((mask & x) == 0)
            res += mask;
        mask <<= 1;
    }
    return res;
}
```

</details>

## Yet Another Minimax Problem
Problem Link: https://hackerrank.com/challenges/yet-another-minimax-problem/problem

<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## Sansa and XOR
Problem Link: https://hackerrank.com/challenges/sansa-and-xor/problem

<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def sansaXor(arr):
    res = 0
    for i in range(len(arr)):
        t = (i + 1) * (len(arr) - i)
        if t % 2 == 1:
            res ^= arr[i]
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int sansaXor(vector<int> &arr) {
    int res = 0;
    for (int i=0; i<size(arr); i++) {
        long t = (i + 1) * (size(arr) - i);
        if (t % 2 == 1)
            res ^= arr[i];
    }
    return res;
}
```

</details>

## AND Product
Problem Link: https://hackerrank.com/challenges/and-product/problem

<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>

## Winning Lottery Ticket
Problem Link: https://hackerrank.com/challenges/winning-lottery-ticket/problem

<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>

## Cipher
Problem Link: https://hackerrank.com/challenges/cipher/problem

<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>

## What's Next?
Problem Link: https://hackerrank.com/challenges/whats-next/problem

<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>

## A or B
Problem Link: https://hackerrank.com/challenges/aorb/problem

<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
#TODO
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
//TODO
```

</details>
