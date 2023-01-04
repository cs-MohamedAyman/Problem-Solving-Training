<a href="/level-2/hackerrank/data-structures/solutions/stacks-queues.md"><img align="right" width="80" src="/logos/hackerrank.jpg"></img></a>

# HackerRank OJ - Data Structures - Stacks & Queues

## Equal Stacks
Problem Link: https://www.hackerrank.com/challenges/equal-stacks/problem

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
Problem Link: https://www.hackerrank.com/challenges/queue-using-two-stacks/problem

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

