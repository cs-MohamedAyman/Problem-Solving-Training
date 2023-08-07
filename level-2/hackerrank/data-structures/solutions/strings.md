<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="80" src="/logos/hackerrank.png"></img></a>

# HackerRank OJ - Data Structures <br> Strings `20 problems`

## Super Reduced String
Problem Link: https://www.hackerrank.com/challenges/reduced-string/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def superReducedString(s):
    stk = []
    for i in s:
        if stk and stk[-1] == i:
            stk.pop()
        else:
            stk.append(i)
    res = ''.join(stk)
    return res if res else 'Empty String'
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
string superReducedString(string s) {
    vector<char> stk;
    for (auto &i : s) {
        if (size(stk) and stk.back() == i)
            stk.pop_back();
        else
            stk.push_back(i);
    }
    string res = "";
    for (auto &i : stk)
        res += i;
    return res != ""? res : "Empty String";
}
```

</details>

## CamelCase
Problem Link: https://www.hackerrank.com/challenges/camelcase/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def camelcase(s):
    res = 1
    alpha = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
    for i in s:
        if i in alpha:
            res += 1
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int camelcase(string s) {
    int res = 1;
    string alpha = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    for (auto &i : s)
        if (alpha.find(i) != -1)
            res ++;
    return res;
}
```

</details>

## Strong Password
Problem Link: https://www.hackerrank.com/challenges/strong-password/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def minimumNumber(n, password):
    numbers = "0123456789"
    lower_case = "abcdefghijklmnopqrstuvwxyz"
    upper_case = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
    special_chars = "!@#$%^&*()-+"
    contain_fn = lambda password, s : any(i in s for i in password) == False
    res = 0
    res += contain_fn(password, numbers)
    res += contain_fn(password, lower_case)
    res += contain_fn(password, upper_case)
    res += contain_fn(password, special_chars)
    return max(res, 6-n)
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int minimumNumber(int n, string password) {
    string numbers = "0123456789";
    string lower_case = "abcdefghijklmnopqrstuvwxyz";
    string upper_case = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    string special_chars = "!@#$%^&*()-+";
    auto contain_fn = [password](string s) {
        bool res = true;
        for (auto &i : password)
            res &= s.find(i) == -1;
        return res;
    };
    int res = 0;
    res += contain_fn(numbers);
    res += contain_fn(lower_case);
    res += contain_fn(upper_case);
    res += contain_fn(special_chars);
    return max(res, 6-n);
}
```

</details>

## Two Characters
Problem Link: https://www.hackerrank.com/challenges/two-characters/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def validate(a, b, s):
    last_a, last_b = 0, 0
    str_len = 0
    for i in range(len(s)):
        if s[i] == a:
            if last_a:
                return 0
            last_a = 1
            last_b = 0
            str_len += 1
        elif s[i] == b:
            if last_b:
                return 0
            last_a = 0
            last_b = 1
            str_len += 1
    return str_len

def alternate(s):
    str_set = list(set(s))
    res = 0
    for i in range(len(str_set)-1):
        for j in range(i+1, len(str_set)):
            res = max(res, validate(str_set[i], str_set[j], s))
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int validate(char a, char b, string s) {
    bool last_a = 0, last_b = 0;
    int str_len = 0;
    for (int i = 0; i < size(s); i++) {
        if (s[i] == a) {
            if (last_a)
                return 0;
            last_a = 1;
            last_b = 0;
            str_len ++;
        }
        else if (s[i] == b) {
            if (last_b)
                return 0;
            last_a = 0;
            last_b = 1;
            str_len ++;
        }
    }
    return str_len;
}
int alternate(string s) {
    bool alpha[26] = {0};
    vector<char> str_set;
    for (int i = 0; i < size(s); i++) {
        if (not alpha[s[i] - 'a']) {
            alpha[s[i] - 'a'] = 1;
            str_set.push_back(s[i]);
        }
    }
    int res = 0;
    for (int i = 0; i < size(str_set)-1; i++)
        for (int j = i+1; j < size(str_set); j++)
            res = max(res, validate(str_set[i], str_set[j], s));
    return res;
}
```

</details>

## Caesar Cipher
Problem Link: https://www.hackerrank.com/challenges/caesar-cipher-1/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def shift_alpha(c, k):
    if ord('A') <= c <= ord('Z'):
        c += k
        if c < ord('A'):
            c += 26
        elif c > ord('Z'):
            c -= 26
    elif ord('a') <= c <= ord('z'):
        c += k
        if c < ord('a'):
            c += 26
        elif c > ord('z'):
            c -= 26
    return chr(c)

def caesarCipher(s, k):
    res = ''
    k %= 26
    for i in s:
        res += shift_alpha(ord(i), k)
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
char shift_alpha(int c, int k) {
    if ('A' <= c and c <= 'Z') {
        c += k;
        if (c < 'A')
            c += 26;
        else if (c > 'Z')
            c -= 26;
    }
    else if ('a' <= c and c <= 'z') {
        c += k;
        if (c < 'a')
            c += 26;
        else if (c > 'z')
            c -= 26;
    }
    return char(c);
}
string caesarCipher(string s, int k) {
    string res = "";
    k %= 26;
    for (auto &i : s)
        res += shift_alpha(int(i), k);
    return res;
}
```

</details>

## Mars Exploration
Problem Link: https://www.hackerrank.com/challenges/mars-exploration/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def marsExploration(s):
    res, j = 0, 0
    tmp = ('S', 'O', 'S')
    for i in range(len(s)):
        if j == 3:
            j = 0
        if s[i] != tmp[j]:
            res += 1
        j += 1
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int marsExploration(string s) {
    int res = 0, j = 0;
    char tmp[] = {'S', 'O', 'S'};
    for (int i=0; i<size(s); i++) {
        if (j == 3)
            j = 0;
        if (s[i] != tmp[j])
            res ++;
        j ++;
    }
    return res;
}
```

</details>

## HackerRank in a String!
Problem Link: https://www.hackerrank.com/challenges/hackerrank-in-a-string/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def hackerrankInString(s):
    word = ['k', 'n', 'a', 'r', 'r', 'e', 'k', 'c', 'a', 'h']
    for i in range(len(s)):
        if not word:
            break
        elif s[i] == word[-1]:
            word.pop()
    return "YES" if not word else "NO"
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
string hackerrankInString(string s) {
    vector<char> word = {'k', 'n', 'a', 'r', 'r', 'e', 'k', 'c', 'a', 'h'};
    for (int i = 0; i < size(s); i++) {
        if (not size(word))
            break;
        else if (s[i] == word[size(word) - 1])
            word.pop_back();
    }
    return not size(word)? "YES" : "NO";
}
```

</details>

## Pangrams
Problem Link: https://www.hackerrank.com/challenges/pangrams/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def pangrams(s):
    if len(s) < 26:
        return "not pangram"
    cnt = [0] * 26
    for i in s:
        if 'A' <= i <= 'Z':
            cnt[ord(i) - ord('A')] += 1
        elif 'a' <= i <= 'z':
            cnt[ord(i) - ord('a')] += 1
    return "not pangram" if 0 in cnt else "pangram"
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
string pangrams(string s) {
    if (size(s) < 26)
        return "not pangram";
    vector<int> cnt(26, 0);
    for (auto &i : s) {
        if ('A' <= i and i <= 'Z')
            cnt[i - 'A'] ++;
        else if ('a' <= i and i <= 'z')
            cnt[i - 'a'] ++;
    }
    return find(cnt.begin(), cnt.end(), 0) == cnt.end()? "pangram" : "not pangram";
}
```

</details>

## Weighted Uniform Strings
Problem Link: https://www.hackerrank.com/challenges/weighted-uniform-string/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def weightedUniformStrings(s, queries):
    alpha_idx = {}
    for i in range(26):
        alpha_idx[chr(i+ord('a'))] = i+1
    uniforms = {}
    mult = 1
    prev_i = 0
    for i in s:
        if i == prev_i:
            mult += 1
        else:
            mult = 1
        uniforms[alpha_idx[i] * mult] = True
        prev_i = i
    j = 0
    res = [''] * len(queries)
    for i in queries:
        res[j] = ("Yes" if i in uniforms else "No")
        j += 1
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
vector<string> weightedUniformStrings(string s, vector<int> queries) {
    map<char, int> alpha_idx;
    for (int i=0; i<26; i++)
        alpha_idx[i+'a'] = i+1;
    map<int, bool> uniforms;
    int mult = 1;
    char prev_i = 0;
    for (auto &i : s) {
        if (i == prev_i)
            mult ++;
        else
            mult = 1;
        uniforms[alpha_idx[i] * mult] = true;
        prev_i = i;
    }
    int j = 0;
    vector<string> res(size(queries));
    for (auto &i : queries) {
        res[j] = uniforms[i]? "Yes" : "No";
        j ++;
    }
    return res;
}
```

</details>

## Separate the Numbers
Problem Link: https://www.hackerrank.com/challenges/separate-the-numbers/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def validate(s, f):
    while s:
        if s[:len(f)] == f:
            s = s[len(f):]
            f = str(int(f) + 1)
        else:
            return False
    return True

def separateNumbers(s):
    if s[0] == '0' and len(s) > 1:
        return "NO"
    for i in range(1, len(s)//2 + 1):
        f = s[:i]
        if validate(s, f):
            return "YES " + f
    return "NO"
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
bool validate(string s, string f) {
    while (size(s)) {
        if (s.substr(0, size(f)) == f) {
            s = s.substr(size(f));
            f = to_string(stol(f) + 1);
        }
        else
            return false;
    }
    return true;
}
string separateNumbers(string s) {
    if (s[0] == '0' and size(s) > 1)
        return "NO";
    for (int i=1 ;i<size(s)/2+1; i++) {
        string f = s.substr(0, i);
        if (validate(s, f))
            return "YES " + f;
    }
    return "NO";
}
```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## ProblemName
Problem Link: ProblemLink

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

