<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="80" src="/logos/hackerrank.png"></img></a>

# HackerRank OJ - Algorithms Basics <br> Implementation I `20 problems`

## Grading Students
Problem Link: https://hackerrank.com/challenges/grading/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def gradingStudents(grades):
    res = []
    for i in grades:
        c = i % 5
        if i >= 38 and 5-c < 3 and c != 0:
            res.append(min(i + 5 - c, 100))
        else:
            res.append(i)
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
vector<int> gradingStudents(vector<int> grades) {
    vector<int> res;
    for (auto &i : grades) {
        int c = i % 5;
        if (i >= 38 and 5-c < 3 and c != 0)
            res.push_back(min(i + 5 - c, 100));
        else
            res.push_back(i);
    }
    return res;
}
```

</details>

## Apple and Orange
Problem Link: https://hackerrank.com/challenges/apple-and-orange/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def countApplesAndOranges(s, t, a, b, apples, oranges):
    res1, res2 = 0, 0
    for i in apples:
        if s <= a + i < t+1:
            res1 += 1
    for i in oranges:
        if s <= b + i < t+1:
            res2 += 1
    print(res1, res2, sep='\n')
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
void countApplesAndOranges(int s, int t, int a, int b, vector<int> &apples, vector<int> &oranges) {
    int res1 = 0, res2 = 0;
    for (auto &i : apples) {
        if (s <= a + i and a + i < t+1)
            res1 ++;
    }
    for (auto &i : oranges) {
        if (s <= b + i and b + i < t+1)
            res2 ++;
    }
    cout << res1 << '\n' << res2;
}
```

</details>

## Number Line Jumps
Problem Link: https://hackerrank.com/challenges/kangaroo/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def kangaroo(x1, v1, x2, v2):
    if x1 == x2:
        return "YES"
    if v1 == v2:
        return "NO"
    xdiff = x1 - x2
    vdiff = v2 - v1
    if (xdiff < 0 and vdiff < 0) or (xdiff > 0 and vdiff > 0):
        mod1 = xdiff % vdiff
        mod2 = vdiff % xdiff
        if mod1 == 0 or mod2 == 0:
            return "YES"
    return "NO"
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
string kangaroo(int x1, int v1, int x2, int v2) {
    if (x1 == x2)
        return "YES";
    if (v1 == v2)
        return "NO";
    int xdiff = x1 - x2;
    int vdiff = v2 - v1;
    if ((xdiff < 0 and vdiff < 0) or (xdiff > 0 and vdiff > 0)) {
        int mod1 = xdiff % vdiff;
        int mod2 = vdiff % xdiff;
        if (mod1 == 0 or mod2 == 0)
            return "YES";
    }
    return "NO";
}
```

</details>

## Between Two Sets
Problem Link: https://hackerrank.com/challenges/between-two-sets/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def getTotalX(a, b):
    res = 0
    for i in range(max(a), min(b)+1):
        all_a = True
        for j in a:
            if i % j != 0:
                all_a = False
        all_b = True
        for j in b:
            if j % i != 0:
                all_b = False
        res += int(all_a and all_b)
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int getTotalX(vector<int> a, vector<int> b) {
    int res = 0;
    int max_a = *max_element(a.begin(), a.end());
    int min_b = *min_element(b.begin(), b.end());
    for (int i=max_a; i<min_b+1; i++) {
        bool all_a = true;
        for (auto &j : a) {
            if (i % j != 0)
                all_a = false;
        }
        bool all_b = true;
        for (auto &j : b) {
            if (j % i != 0)
                all_b = false;
        }
        res += int(all_a and all_b);
    }
    return res;
}
```

</details>

## Breaking the Records
Problem Link: https://hackerrank.com/challenges/breaking-best-and-worst-records/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def breakingRecords(scores):
    maxi, mini = scores[0], scores[0]
    max_cnt, min_cnt = 0, 0
    for i in scores:
        if i > maxi:
            maxi = i
            max_cnt += 1
        if i < mini:
            mini = i
            min_cnt += 1
    return [max_cnt, min_cnt]
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
vector<int> breakingRecords(vector<int> scores) {
    int maxi = scores[0], mini = scores[0];
    int max_cnt = 0, min_cnt = 0;
    for (auto &i : scores) {
        if (i > maxi) {
            maxi = i;
            max_cnt ++;
        }
        if (i < mini) {
            mini = i;
            min_cnt ++;
        }
    }
    return {max_cnt, min_cnt};
}
```

</details>

## Subarray Division
Problem Link: https://hackerrank.com/challenges/the-birthday-bar/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def birthday(s, d, m):
    res = 0
    for i in range(len(s)):
        curr_sum = 0
        for j in range(i, min(len(s), m+i)):
            curr_sum += s[j]
        if curr_sum == d:
            res += 1
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int birthday(vector<int> s, int d, int m) {
    int res = 0;
    for (int i=0; i<size(s); i++) {
        int curr_sum = 0;
        for (int j=i; j<min(size(s), m+i); j++)
            curr_sum += s[j];
        if (curr_sum == d)
            res ++;
    }
    return res;
}
```

</details>

## Divisible Sum Pairs
Problem Link: https://hackerrank.com/challenges/divisible-sum-pairs/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def divisibleSumPairs(n, k, arr):
    res = 0
    for i in range(len(arr)):
        for j in range(i+1, len(arr)):
            if (arr[i] + arr[j]) % k == 0:
                res += 1
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int divisibleSumPairs(int n, int k, vector<int> arr) {
    int res = 0;
    for (int i=0; i<size(arr); i++) {
        for (int j=i+1; j<size(arr); j++) {
            if ((arr[i] + arr[j]) % k == 0)
                res ++;
        }
    }
    return res;
}
```

</details>

## Migratory Birds
Problem Link: https://hackerrank.com/challenges/migratory-birds/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def migratoryBirds(arr):
    res = [0] * 6
    for i in arr:
        res[i] += 1
    return res.index(max(res))
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int migratoryBirds(vector<int> arr) {
    vector<int> res(6, 0);
    for (auto &i : arr)
        res[i] ++;
    int max_arr = *max_element(res.begin(), res.end());
    return find(res.begin(), res.end(), max_arr) - res.begin();
}
```

</details>

## Day of the Programmer
Problem Link: https://hackerrank.com/challenges/day-of-the-programmer/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def dayOfProgrammer(year):
    if year == 1918:
        return '26.09.1918'
    elif (year < 1918 and year%4 == 0) or \
         (year%400 == 0 or (year%4 == 0 and year%100 != 0)):
        return '12.09.' + str(year)
    else:
        return '13.09.' + str(year)
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
string dayOfProgrammer(int year) {
    if (year == 1918)
        return "26.09.1918";
    else if ((year < 1918 and year%4 == 0) or
             (year%400 == 0 or (year%4 == 0 and year%100 != 0)))
        return "12.09." + to_string(year);
    else
        return "13.09." + to_string(year);
}
```

</details>

## Bill Division
Problem Link: https://hackerrank.com/challenges/bon-appetit/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def bonAppetit(bill, k, b):
    total = 0
    for i in range(len(bill)):
        if i == k:
            continue
        total += bill[i]
    x = b - total//2
    if x != 0:
        print(x)
    else:
        print("Bon Appetit")
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
void bonAppetit(vector<int> bill, int k, int b) {
    int total = 0;
    for (int i=0; i<size(bill); i++) {
        if (i == k)
            continue;
        total += bill[i];
    }
    int x = b - total/2;
    if (x != 0)
        cout << x;
    else
        cout << "Bon Appetit";
}
```

</details>

## Sales by Match
Problem Link: https://hackerrank.com/challenges/sock-merchant/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def sockMerchant(n, arr):
    res = 0
    set_arr = set(arr)
    for i in set_arr:
        res += arr.count(i)//2
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int sockMerchant(int n, vector<int> arr) {
    int res = 0;
    set<int> set_arr(arr.begin(), arr.end());
    for (auto &i : set_arr)
        res += count(arr.begin(), arr.end(), i)/2;
    return res;
}
```

</details>

## Drawing Book
Problem Link: https://hackerrank.com/challenges/drawing-book/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def pageCount(n, p):
    return min(p//2, n//2 - p//2)
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int pageCount(int n, int p) {
    return min(p/2, n/2 - p/2);
}
```

</details>

## Counting Valleys
Problem Link: https://hackerrank.com/challenges/counting-valleys/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def countingValleys(steps, path):
    res, curr = 0, 0
    for i in range(len(path)):
        if path[i] == 'D':
            curr -= 1
        elif path[i] == 'U':
            curr += 1
        if path[i] == 'U' and curr == 0:
            res += 1
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int countingValleys(int steps, string path) {
    int res = 0, curr = 0;
    for (int i=0; i<size(path); i++) {
        if (path[i] == 'D')
            curr --;
        else if (path[i] == 'U')
            curr ++;
        if (path[i] == 'U' and curr == 0)
            res ++;
    }
    return res;
}
```

</details>

## Electronics Shop
Problem Link: https://hackerrank.com/challenges/electronics-shop/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def getMoneySpent(keyboards, drives, b):
    keyboards.sort()
    drives.sort()
    res = -1
    for k in keyboards:
        x = -1
        for d in drives:
            if k + d > b:
                break
            x = k + d
        if x == -1:
            break
        res = max(res, x)
    return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int getMoneySpent(vector<int> keyboards, vector<int> drives, int b) {
    sort(keyboards.begin(), keyboards.end());
    sort(drives.begin(), drives.end());
    int res = -1;
    for (auto &k : keyboards) {
        int x = -1;
        for (auto &d : drives) {
            if (k + d > b)
                break;
            x = k + d;
        }
        if (x == -1)
            break;
        res = max(res, x);
    }
    return res;
}
```

</details>

## Cats and a Mouse
Problem Link: https://hackerrank.com/challenges/cats-and-a-mouse/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def catAndMouse(x, y, z):
    a = abs(x - z)
    b = abs(y - z)
    if a < b:
        return "Cat A"
    elif a > b:
        return "Cat B"
    else:
        return "Mouse C"
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
string catAndMouse(int x, int y, int z) {
    int a = abs(x - z);
    int b = abs(y - z);
    if (a < b)
        return "Cat A";
    else if (a > b)
        return "Cat B";
    else
        return "Mouse C";
}
```

</details>

## The Hurdle Race
Problem Link: https://hackerrank.com/challenges/the-hurdle-race/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def hurdleRace(k, height):
    return max(0, max(height) - k)
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int hurdleRace(int k, vector<int> height) {
    int max_item = *max_element(height.begin(), height.end());
    return max(0, max_item - k);
}
```

</details>

## Designer PDF Viewer
Problem Link: https://hackerrank.com/challenges/designer-pdf-viewer/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def designerPdfViewer(h, word):
    max_item = 0
    for i in word:
        max_item = max(max_item, h[ord(i) - ord('a')])
    return max_item * len(word)
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int designerPdfViewer(vector<int> h, string word) {
    int max_item = 0;
    for (auto &i : word)
        max_item = max(max_item, h[i - 'a']);
    return max_item * size(word);
}
```

</details>

## Utopian Tree
Problem Link: https://hackerrank.com/challenges/utopian-tree/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def utopianTree(n):
    height = 1
    for i in range(n):
        if i%2 == 1:
            height += 1
        else:
            height *= 2
    return height
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int utopianTree(int n) {
    int height = 1;
    for (int i=0 ; i<n ; i++) {
        if (i%2 == 1)
            height ++;
        else
            height *= 2;
    }
    return height;
}
```

</details>

## Angry Professor
Problem Link: https://hackerrank.com/challenges/angry-professor/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def angryProfessor(k, a):
    sum_arr = 0
    for i in a:
        sum_arr += int(i <= 0)
    return "YES" if sum_arr < k else "NO"
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
string angryProfessor(int k, vector<int> a) {
    int sum_arr = 0;
    for (auto &i : a)
        sum_arr += int(i <= 0);
    return (sum_arr < k? "YES" : "NO");
}
```

</details>

## Minimum Distances
Problem Link: https://www.hackerrank.com/challenges/minimum-distances/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def minimumDistances(a):
    res = 2e9
    for i in range(len(a)):
        for j in range(i+1, len(a)):
            if a[i] == a[j] and res > j-i:
                res = j-i
    if res == 2e9:
        return -1
    else:
        return res
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/implementation-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int minimumDistances(vector<int> a) {
    int res = 2e9;
    for (int i = 0; i < size(a); i++) {
        for (int j = i+1; j < size(a); j++) {
            if (a[i] == a[j] and res > j-i)
                res = j-i;
        }
    }
    if (res == 2e9) 
        return -1;
    else
        return res;
}
```

</details>
