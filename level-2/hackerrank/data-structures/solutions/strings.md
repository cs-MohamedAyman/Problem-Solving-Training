<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="80" src="/logos/hackerrank.png"></img></a>

# HackerRank OJ - Data Structures <br> Strings `20 problems`

## Super Reduced String
Problem Link: https://hackerrank.com/challenges/reduced-string/problem

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
Problem Link: https://hackerrank.com/challenges/camelcase/problem

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
Problem Link: https://hackerrank.com/challenges/strong-password/problem

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
Problem Link: https://hackerrank.com/challenges/two-characters/problem

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
Problem Link: https://hackerrank.com/challenges/caesar-cipher-1/problem

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
Problem Link: https://hackerrank.com/challenges/mars-exploration/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def marsExploration(s):
    res, j = 0, 0
    temp = ('S', 'O', 'S')
    for i in range(len(s)):
        if j == 3:
            j = 0
        if s[i] != temp[j]:
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
    char temp[] = {'S', 'O', 'S'};
    for (int i=0; i<size(s); i++) {
        if (j == 3)
            j = 0;
        if (s[i] != temp[j])
            res ++;
        j ++;
    }
    return res;
}
```

</details>

## HackerRank in a String!
Problem Link: https://hackerrank.com/challenges/hackerrank-in-a-string/problem

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
Problem Link: https://hackerrank.com/challenges/pangrams/problem

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
Problem Link: https://hackerrank.com/challenges/weighted-uniform-string/problem

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
vector<string> weightedUniformStrings(string s, vector<int> &queries) {
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
Problem Link: https://hackerrank.com/challenges/separate-the-numbers/problem

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

## Alternating Characters
Problem Link: https://hackerrank.com/challenges/alternating-characters/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def alternatingCharacters(s):
    res = 0
    for i in range(1, len(s)):
        if s[i] == s[i-1]:
            res += 1
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int alternatingCharacters(string s) {
    int res = 0;
    for (int i=1; i<size(s); i++)
        if (s[i] == s[i-1])
            res ++;
    return res;
}
```

</details>

## Beautiful Binary String
Problem Link: https://hackerrank.com/challenges/beautiful-binary-string/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def beautifulBinaryString(b):
    res = 0
    s = list(b)
    for i in range(2, len(s)):
        if s[i] == '0' and s[i-1] == '1' and s[i-2] == '0':
            s[i] = '1'
            res += 1
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int beautifulBinaryString(string b) {
    int res = 0;
    vector<char> s(b.begin(), b.end());
    for (int i=2; i<size(s); i++) {
        if (s[i] == '0' and s[i-1] == '1' and s[i-2] == '0') {
            s[i] = '1';
            res ++;
        }
    }
    return res;
}
```

</details>

## The Love-Letter Mystery
Problem Link: https://hackerrank.com/challenges/the-love-letter-mystery/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def theLoveLetterMystery(s):
    res = 0
    for i in range(len(s)//2):
        if s[i] != s[-i-1]:
            res += abs(ord(s[i]) - ord(s[-i-1]))
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int theLoveLetterMystery(string s) {
    int res = 0;
    for (int i=0; i<size(s)/2; i++)
        if (s[i] != s[size(s)-i-1])
            res += abs(s[i] - s[size(s)-i-1]);
    return res;
}
```

</details>

## Palindrome Index
Problem Link: https://hackerrank.com/challenges/palindrome-index/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def palindromeIndex(s):
    for i in range(len(s)//2):
        if s[i] != s[-i-1]:
            t = s[:i]+s[i+1:]
            if t == t[::-1]:
                return i
            else:
                return len(s)-i-1
    return -1
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int palindromeIndex(string s) {
    for (int i=0; i<size(s)/2; i++) {
        if (s[i] != s[size(s)-i-1]) {
            string t = s.substr(0, i) + s.substr(i+1);
            string w = t;
            reverse(w.begin(), w.end());
            if (t == w)
                return i;
            else
                return size(s)-i-1;
        }
    }
    return -1;
}
```

</details>

## Anagram
Problem Link: https://hackerrank.com/challenges/anagram/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def anagram(s):
    if len(s) % 2 == 1:
        return -1
    arr = list(s)
    a = arr[:len(arr)//2]
    b = arr[len(arr)//2:]
    res = 0
    for i in range(len(a)):
        if a[i] in b:
            b.remove(a[i])
        else:
            res += 1
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int anagram(string s) {
    if (size(s) % 2 == 1)
        return -1;
    vector<char> arr(s.begin(), s.end());
    vector<char> a(arr.begin(), arr.begin()+size(arr)/2);
    vector<char> b(arr.begin()+size(arr)/2, arr.end());
    int res = 0;
    for (int i=0; i<size(a); i++) {
        if (find(b.begin(), b.end(), a[i]) != b.end())
            b.erase(find(b.begin(), b.end(), a[i]));
        else
            res ++;
    }
    return res;
}
```

</details>

## Making Anagrams
Problem Link: https://hackerrank.com/challenges/making-anagrams/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def makingAnagrams(s1, s2):
    cnt_a = {i : s1.count(i) for i in set(s1)}
    cnt_b = {i : s2.count(i) for i in set(s2)}
    diff_a = {i : max(0, cnt_a[i] - cnt_b.get(i, 0)) for i in cnt_a}
    diff_b = {i : max(0, cnt_b[i] - cnt_a.get(i, 0)) for i in cnt_b}
    res = sum(diff_a.values()) + sum(diff_b.values())
    return res
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int makingAnagrams(string s1, string s2) {
    auto fill_cnt = [](string &s) {
        map<char, int> cnt;
        for (auto &i : set<char>(s.begin(), s.end()))
            cnt[i] = count(s.begin(), s.end(), i);
        return cnt;
    };
    map<char, int> cnt_a = fill_cnt(s1);
    map<char, int> cnt_b = fill_cnt(s2);
    auto calc_diff = [](map<char, int> &cnt1, map<char, int> &cnt2) {
        map<char, int> diff;
        for (auto &[i, j] : cnt1)
            diff[i] = max(0, cnt1[i] - cnt2[i]);
        return diff;
    };
    auto calc_sum = [](map<char, int> diff) {
        int res = 0;
        for (auto &[i, j] : diff)
            res += j;
        return res;
    };
    return calc_sum(calc_diff(cnt_a, cnt_b)) + calc_sum(calc_diff(cnt_b, cnt_a));
}
```

</details>

## Game of Thrones - I
Problem Link: https://hackerrank.com/challenges/game-of-thrones/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def gameOfThrones(s):
    cnt = {i : s.count(i) for i in set(s)}
    sum_odds = lambda cnt : sum(cnt[i]%2 == 1 for i in cnt)
    return 'YES' if sum_odds(cnt) < 2 else 'NO'
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
string gameOfThrones(string s) {
    auto fill_cnt = [](string &s) {
        map<char, int> cnt;
        for (auto &i : set<char>(s.begin(), s.end()))
            cnt[i] = count(s.begin(), s.end(), i);
        return cnt;
    };
    auto sum_odds = [](map<char, int> cnt) {
        int res = 0;
        for (auto &[i, j] : cnt)
            res += (j%2 == 1);
        return res;
    };
    return sum_odds(fill_cnt(s)) < 2? "YES" : "NO";
}
```

</details>

## Two Strings
Problem Link: https://hackerrank.com/challenges/two-strings/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def twoStrings(s1, s2):
    return 'YES' if set(s1) & set(s2) else 'NO'
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
string twoStrings(string s1, string s2) {
    set<int> res;
    sort(s1.begin(), s1.end());
    sort(s2.begin(), s2.end());
    set_intersection(s1.begin(), s1.end(), s2.begin(), s2.end(),
                     inserter(res, res.begin()));
    return size(res) > 0? "YES" : "NO";
}
```

</details>

## String Construction
Problem Link: https://hackerrank.com/challenges/string-construction/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def stringConstruction(s):
    return len(set(s))
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int stringConstruction(string s) {
    return size(set<char>(s.begin(), s.end()));
}
```

</details>

## Funny String
Problem Link: https://hackerrank.com/challenges/funny-string/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def funnyString(s):
    res = s[::-1]
    for i in range(1, len(s)):
        d1 = abs(ord(s[i]) - ord(s[i-1]))
        d2 = abs(ord(res[i]) - ord(res[i-1]))
        if d1 != d2:
            return 'Not Funny'
    return 'Funny'
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
string funnyString(string s) {
    string res = s;
    reverse(res.begin(), res.end());
    for (int i=1; i<size(s); i++) {
        int d1 = abs(s[i] - s[i-1]);
        int d2 = abs(res[i] - res[i-1]);
        if (d1 != d2)
            return "Not Funny";
    }
    return "Funny";
}
```

</details>

## Gemstones
Problem Link: https://hackerrank.com/challenges/gem-stones/problem

<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def gemstones(arr):
    res = set(arr[0])
    for i in arr:
        res = res.intersection(set(i))
    return len(res)
```

</details>
<a href="/level-2/hackerrank/data-structures/solutions/strings.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int gemstones(vector<string> arr) {
    for (auto &i : arr)
        sort(i.begin(), i.end());
    vector<char> v;
    set<char> res(arr[0].begin(), arr[0].end());
    for (auto &i : arr) {
        set_intersection(res.begin(), res.end(), i.begin(), i.end(),
                         inserter(v, v.begin()));
        res = set<char>(v.begin(), v.end());
        v.clear();
    }
    return size(res);
}
```

</details>

