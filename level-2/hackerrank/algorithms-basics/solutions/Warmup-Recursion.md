<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="80" src="/logos/hackerrank.png"></img></a>

# HackerRank OJ - Algorithms Basics <br> Warmup & Recursion `20 problems`

## Simple Array Sum
Problem Link: https://www.hackerrank.com/challenges/simple-array-sum/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def simpleArraySum(arr):
    return sum(arr)
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int simpleArraySum(vector<int> arr) {
    return accumulate(arr.begin(), arr.end(), 0);
}
```

</details>

## Compare the Triplets
Problem Link: https://www.hackerrank.com/challenges/compare-the-triplets/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def compareTriplets(a, b):
    sum1, sum2 = 0, 0
    for i, j in zip(a, b):
        sum1 += int(i > j)
        sum2 += int(i < j)
    return [sum1, sum2]
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
vector<int> compareTriplets(vector<int> a, vector<int> b) {
    int sum1 = 0, sum2 = 0;
    for (int i=0; i<size(a); i++) {
        sum1 += int(a[i] > b[i]);
        sum2 += int(a[i] < b[i]);
    }
    return {sum1, sum2};
}
```

</details>

## A Very Big Sum
Problem Link: https://www.hackerrank.com/challenges/a-very-big-sum/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def aVeryBigSum(arr):
    return sum(arr)
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
long aVeryBigSum(vector<long> arr) {
    return accumulate(arr.begin(), arr.end(), 0LL);
}
```

</details>

## Diagonal Difference
Problem Link: https://www.hackerrank.com/challenges/diagonal-difference/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def diagonalDifference(arr):
    sum1, sum2 = 0, 0
    for i in range(len(arr)):
        sum1 += arr[i][i]
        sum2 += arr[i][len(arr)-i-1]
    return abs(sum1 - sum2)
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int diagonalDifference(vector<vector<int>> arr) {
    int sum1 = 0, sum2 = 0;
    for (int i=0; i<size(arr); i++) {
        sum1 += arr[i][i];
        sum2 += arr[i][size(arr)-i-1];
    }
    return abs(sum1 - sum2);
}
```

</details>

## Plus Minus
Problem Link: https://www.hackerrank.com/challenges/plus-minus/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def plusMinus(arr):
    sum_pos, sum_neg, sum_zero = 0, 0, 0
    for i in arr:
        sum_pos += int(i > 0)
        sum_neg += int(i < 0)
        sum_zero += int(i == 0)
    sum_pos = sum_pos/len(arr)
    sum_neg = sum_neg/len(arr)
    sum_zero = sum_zero/len(arr)
    print(sum_pos, sum_neg, sum_zero, sep='\n')
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
void plusMinus(vector<int> arr) {
    double sum_pos = 0, sum_neg = 0, sum_zero = 0;
    for (int &i : arr) {
        sum_pos += int(i > 0);
        sum_neg += int(i < 0);
        sum_zero += int(i == 0);
    }
    sum_pos = sum_pos/size(arr);
    sum_neg = sum_neg/size(arr);
    sum_zero = sum_zero/size(arr);
    cout << sum_pos << '\n' << sum_neg << '\n' << sum_zero;
}
```

</details>

## Staircase
Problem Link: https://www.hackerrank.com/challenges/staircase/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def staircase(n):
    for i in range(n):
        print(' '*(n-i-1)+'#'*(i+1))
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
void staircase(int n) {
    for (int i=0; i<n; i++)
        cout << string(n-i-1, ' ') + string(i+1, '#') << '\n';
}
```

</details>

## Mini-Max Sum
Problem Link: https://www.hackerrank.com/challenges/mini-max-sum/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def miniMaxSum(arr):
    sum_arr = [sum(arr)] * 5
    for i in range(5):
        sum_arr[i] -= arr[i]
    print(min(sum_arr), max(sum_arr))
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
void miniMaxSum(vector<int> arr) {
    long sum = accumulate(arr.begin(), arr.end(), 0LL);
    vector<long> sum_arr(5, sum);
    for (int i=0; i<5; i++)
        sum_arr[i] -= arr[i];
    cout << *min_element(sum_arr.begin(), sum_arr.end()) << ' ';
    cout << *max_element(sum_arr.begin(), sum_arr.end()) << '\n';
}
```

</details>

## Birthday Cake Candles
Problem Link: https://www.hackerrank.com/challenges/birthday-cake-candles/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def birthdayCakeCandles(candles):
    return candles.count(max(candles))
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int birthdayCakeCandles(vector<int> candles) {
    auto it_b = candles.begin();
    auto it_e = candles.end();
    return count(it_b, it_e, *max_element(it_b, it_e));
}
```

</details>

## Time Conversion
Problem Link: https://www.hackerrank.com/challenges/time-conversion/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def timeConversion(s):
    if s[-2:] == 'AM' and s[:2] == '12':
        s = '00' + s[2:]
    if s[-2:] == 'PM' and s[:2] != '12':
        s = str(int(s[:2])+12) + s[2:]
    return s[:-2]
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
string timeConversion(string s) {
    if (s.substr(size(s)-2, 2) == "AM" and s.substr(0, 2) == "12")
        s = "00" + s.substr(2, size(s)-2);
    if (s.substr(size(s)-2, 2) == "PM" and s.substr(0, 2) != "12")
        s = to_string(stoi(s.substr(0, 2))+12) + s.substr(2, size(s)-2);
    return  s.substr(0, size(s)-2);
}
```

</details>

## The Power Sum
Problem Link: https://www.hackerrank.com/challenges/the-power-sum/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def powerSum(X, N):
    def calc_way(n, k, j):
        if n == 0: 
            return 1
        if n < 0: 
            return 0
        res, i = 0, j
        while i ** k <= n:
            res += calc_way(n - i ** k, k, i+1)
            i += 1
        return res
    
    return calc_way(X, N, 1)
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
int calc_way(int n, int k, int j) {
    if (n == 0) 
        return 1;
    if (n < 0) 
        return 0;
    int res = 0, i = j;
    while (pow(i, k) <= n) {
        res += calc_way(n - pow(i, k), k, i+1);
        i ++;
    }
    return res;
}
int powerSum(int X, int N) {
    return calc_way(X, N, 1);
}
```

</details>

## Crossword Puzzle
Problem Link: https://www.hackerrank.com/challenges/crossword-puzzle/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Space:
    def __init__(self, start, length, direction, taken):
        self.start = start
        self.length = length
        self.direction = direction
        self.taken = taken

def next_space(row, col, direction):
    return row + int(direction), col + int(not direction)

def add_word(grid, space, word):
    new_grid = []
    row, col = space.start
    for c in word:
        new_grid.append(grid[row][col])
        grid[row][col] = c
        row, col = next_space(row, col, space.direction)
    return new_grid

def can_add_word(grid, space, word):
    if space.taken or len(word) != space.length:
        return False
    row, col = space.start
    for c in word:
        if not (grid[row][col] == '-' or grid[row][col] == c):
            return False
        row, col = next_space(row, col, space.direction)
    return True

def find_solution(grid, spaces, words):
    if len(words) == 0:
        return True
    for word in words:
        for space in spaces:
            if can_add_word(grid, space, word):
                before = add_word(grid, space, word)
                space.taken = True
                new_words = words.copy()
                new_words.remove(word)
                if find_solution(grid, spaces, new_words):
                    return True
                add_word(grid, space, before)
                space.taken = False
    return False

def where_spaces(line):
    spaces = []
    i = 0
    while i < len(line):
        j = i
        while j < len(line) and line[j] == '-':
            j += 1
        if j - i > 0:
            spaces.append((i, j - i))
        i = j + 1
    return spaces

def count_spaces(lines, direction):
    spaces = []
    for i in range(10):
        for index, length in where_spaces(lines[i]):
            start = (index, i) if direction else (i, index)
            spaces.append(Space(start, length, direction, False))
    return spaces

def crosswordPuzzle(crossword, words):
    rows = [[crossword[i][j] for j in range(10)] for i in range(10)]
    cols = [[crossword[j][i] for j in range(10)] for i in range(10)]
    row_spaces = count_spaces(rows, False)
    col_spaces = count_spaces(cols, True)
    crossword = rows.copy()
    words = set(words.split(';'))
    find_solution(crossword, row_spaces+col_spaces, words)
    crossword = ["".join(row) for row in crossword]
    return crossword
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
struct Space {
    pair<int, int> start;
    int length;
    bool direction, taken;
    Space(pair<int, int> start, int length, bool direction, bool taken) {
        this->start = start;
        this->length = length;
        this->direction = direction;
        this->taken = taken;
    }
};
pair<int, int> next_space(int row, int col, bool direction) {
    return {row + int(direction), col + int(not direction)};
}
string add_word(vector<string> &grid, Space space, string word) {
    string new_grid;
    pair<int, int> point = space.start;
    int row = point.first, col = point.second;
    for (char &c : word) {
        new_grid += grid[row][col];
        grid[row][col] = c;
        point = next_space(row, col, space.direction);
        row = point.first, col = point.second;
    }
    return new_grid;
}
bool can_add_word(vector<string> grid, Space space, string word) {
    if (space.taken or size(word) != space.length)
        return false;
    pair<int, int> point = space.start;
    int row = point.first, col = point.second;
    for (char &c : word) {
        if (not (grid[row][col] == '-' or grid[row][col] == c))
            return false;
        point = next_space(row, col, space.direction);
        row = point.first, col = point.second;
    }
    return true;
}
bool find_solution(vector<string> &grid, vector<Space> spaces, set<string> words) {
    if (size(words) == 0)
        return true;
    for (string word : words) {
        for (Space &space : spaces) {
            if (can_add_word(grid, space, word)) {
                string before = add_word(grid, space, word);
                space.taken = true;
                set<string> new_words = words;
                new_words.erase(*new_words.find(word));
                if (find_solution(grid, spaces, new_words))
                    return true;
                add_word(grid, space, before);
                space.taken = false;
            }
        }
    }
    return false;
}
vector<pair<int, int>> where_spaces(string line) {
    vector<pair<int, int>> spaces;
    int i = 0;
    while (i < size(line)) {
        int j = i;
        while (j < size(line) and line[j] == '-')
            j ++;
        if (j - i > 0)
            spaces.push_back({i, j - i});
        i = j + 1;
    }
    return spaces;
}
vector<Space> count_spaces(vector<string> lines, bool direction) {
    vector<Space> spaces;
    pair<int, int> start;
    for (int i=0; i<10; i++) {
        for (auto &[index, length] : where_spaces(lines[i])) {
            direction? start = {index, i} : start = {i, index};
            spaces.push_back(Space(start, length, direction, false));
        }
    }
    return spaces;
}
set<string> split(string s, char sep) {
    int i = 0;
    string temp = "";
    set<string> res;
    while (i < size(s)) {
        if (s[i] != sep)
            temp += s[i]; 
        else {
            res.insert(temp);
            temp.clear();
        }
        i++;
    }
    res.insert(temp);
    return res;
}
vector<string> grid_as_rows(vector<string> &crossword) {
    vector<string> rows(10); 
    for (int i=0; i<10; i++) {
        string temp = "";
        for (int j=0; j<10; j++)
            temp += crossword[i][j];
        rows[i] = temp;
    }
    return rows;
}
vector<string> grid_as_cols(vector<string> &crossword) {
    vector<string> cols(10); 
    for (int i=0; i<10; i++) {
        string temp = "";
        for (int j=0; j<10; j++)
            temp += crossword[j][i];
        cols[i] = temp;
    }
    return cols;
}
vector<string> crosswordPuzzle(vector<string> crossword, string words) {
    vector<string> rows = grid_as_rows(crossword);
    vector<string> cols = grid_as_cols(crossword);
    vector<Space> row_spaces = count_spaces(rows, false);
    vector<Space> col_spaces = count_spaces(cols, true);
    crossword = rows;
    set<string> words_sep = split(words, ';');
    vector<Space> all_spaces = row_spaces;
    all_spaces.insert(all_spaces.end(), col_spaces.begin(), col_spaces.end());
    find_solution(crossword, all_spaces, words_sep);
    return crossword;
}
```

</details>

## Recursive Digit Sum
Problem Link: https://www.hackerrank.com/challenges/recursive-digit-sum/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def superDigit(n, k):
    def get_super_digit(p):
        if len(p) == 1:
            return int(p)
        digits = map(int, list(p))
        return get_super_digit(str(sum(digits)))

    digits = map(int, list(n))
    return get_super_digit(str(sum(digits) * k))
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
vector<int> map_string_to_list(string s) {
    vector<int> res(s.begin(), s.end());
    for (int &i : res)
        i -= '0';
    return res;
}
int get_super_digit(string p) {
    if (size(p) == 1)
        return p[0] - '0';
    vector<int> digits = map_string_to_list(p);
    int sum = accumulate(digits.begin(), digits.end(), 0);
    return get_super_digit(to_string(sum));
}
int superDigit(string n, int k) {
    vector<int> digits = map_string_to_list(n);
    int sum = accumulate(digits.begin(), digits.end(), 0);
    string s = "";
    for (int i=0; i<k; i++)
        s += to_string(sum);
    return get_super_digit(s);
}
```

</details>

## Simplified Chess Engine
Problem Link: https://www.hackerrank.com/challenges/simplified-chess-engine/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## Password Cracker
Problem Link: https://www.hackerrank.com/challenges/password-cracker/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## Stone Division, Revisited
Problem Link: https://www.hackerrank.com/challenges/stone-division-2/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## Arithmetic Expressions
Problem Link: https://www.hackerrank.com/challenges/arithmetic-expressions/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## K Factorization
Problem Link: https://www.hackerrank.com/challenges/k-factorization/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
def kFactorization(n, A):
    def k_factorization(n, arr, i, res):
        if i == n:
            all_res.append(res[:])
            return True
        if i > n:
            return False
        for j in range(len(arr)):
            res.append(i * arr[j])
            k_factorization(n, arr[j:], i * arr[j], res)
            res.pop()
        return False

    all_res = []
    A = sorted(A)
    k_factorization(n, A, 1, [1])
    if all_res:
        return min(all_res, key=len)
    else:
        return [-1]
```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
auto cmp = [](const vector<int> &a, const vector<int> &b) { 
    return size(a) < size(b);
};
set<vector<int>, decltype(cmp)> all_res(cmp);

bool k_factorization(int n, vector<int> arr, long i, vector<int> res) {
    if (i == n) {
        all_res.insert(res);
        return true;
    }
    if (i > n)
        return false;
    for (int j=0; j<size(arr); j++) {
        res.push_back(i * arr[j]);
        vector<int> temp(arr.begin()+j, arr.end());
        k_factorization(n, temp, i * arr[j], res);
        res.pop_back();
    }
    return false;
}
vector<int> kFactorization(int n, vector<int> A) {
    sort(A.begin(), A.end());
    k_factorization(n, A, 1, {1});
    if (size(all_res))
        return *all_res.begin();
    else
        return {-1};
}
```

</details>

## Bowling Pins
Problem Link: https://www.hackerrank.com/challenges/bowling-pins/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## Simplified Chess Engine II
Problem Link: https://www.hackerrank.com/challenges/simplified-chess-engine-ii/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## Repetitive K-Sums
Problem Link: https://www.hackerrank.com/challenges/repeat-k-sums/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/hackerrank/algorithms-basics/solutions/warmup-recursion.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>
