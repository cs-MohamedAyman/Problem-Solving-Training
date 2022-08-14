<img align="right" width="80" src="https://github.com/cs-MohamedAyman/Problem-Solving-Training/blob/master/logos/leetcode.jpg">

## LeetCode OJ - Phase 4 Interviews Questions - Hard Problems

### first missing positive:
Problem Link: https://leetcode.com/problems/first-missing-positive

#### - Python Solution
```python
class Solution:
    def firstMissingPositive(self, nums: List[int]) -> int:
        for i in range(len(nums)):
            if nums[i] < 0:
                nums[i] = 0
        for i in range(len(nums)):
            val = abs(nums[i])
            if 1 <= val <= len(nums):
                if nums[val-1] > 0:
                    nums[val-1] *= -1
                elif nums[val-1] == 0:
                    nums[val-1] = -(len(nums)+1)
        for i in range(len(nums)):
            if nums[i] >= 0:
                return i+1
        return len(nums)+1
```
#### - CPP Solution
```cpp
class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        for (int i=0; i<size(nums); i++) {
            if (nums[i] < 0)
                nums[i] = 0;
        }
        for (int i=0; i<size(nums); i++) {
            int val = abs(nums[i]);
            if (1 <= val and val <= size(nums)) {
                if (nums[val-1] > 0)
                    nums[val-1] *= -1;
                else if (nums[val-1] == 0)
                    nums[val-1] = -(size(nums)+1);
            }
        }
        for (int i=0; i<size(nums); i++) {
            if (nums[i] >= 0)
                return i+1;
        }
        return size(nums)+1;
    }
};
```

### sudoku solver:
Problem Link: https://leetcode.com/problems/sudoku-solver

#### - Python Solution
```python
class Solution:
    def solveSudoku(self, grid: List[List[str]]) -> None:
        def check_valid_value(i, j, v):
            for k in range(9):
                if grid[i][k] == v or grid[k][j] == v:
                    return False
            b, e = i//3*3, j//3*3
            for k in range(b, b+3):
                for w in range(e, e+3):
                    if grid[k][w] == v:
                        return False
            return True

        def solve_grid(i, j):
            if j == 9:
                i += 1
                j = 0
            if i == 9:
                return True
            if cpy_grid[i][j] != '.':
                return solve_grid(i, j+1)
            for k in range(1, 10):
                t = chr(k+ord('0'))
                if check_valid_value(i, j, t):
                    grid[i][j] = t
                    cpy_grid[i][j] = t
                    if solve_grid(i, j+1):
                        return True
                    grid[i][j] = '.'
                    cpy_grid[i][j] = '.'
            return False

        cpy_grid = [[i for i in j] for j in grid]
        solve_grid(0, 0)
```
#### - CPP Solution
```cpp
class Solution {
    bool check_valid_value(vector<vector<char>> &grid, int i, int j, int v) {
        for (int k = 0; k < 9; k++)
            if (grid[i][k] == v or grid[k][j] == v)
                return false;
        int b = i/3*3, e = j/3*3;
        for (int k = b; k < b+3; k++)
            for (int w = e; w < e+3; w++)
                if (grid[k][w] == v)
                    return false;
        return true;
    }
    bool solve_grid(vector<vector<char>> &cpy_grid, vector<vector<char>> &grid, int i, int j) {
        if (j == 9) {
            i += 1;
            j = 0;
        }
        if (i == 9)
            return true;
        if (cpy_grid[i][j] != '.')
            return solve_grid(cpy_grid, grid, i, j+1);
        for (int k = 1; k < 10; k++) {
            char t = k+'0';
            if (check_valid_value(grid, i, j, t)) {
                grid[i][j] = t;
                cpy_grid[i][j] = t;
                if (solve_grid(cpy_grid, grid, i, j+1))
                    return true;
            }
            grid[i][j] = '.';
            cpy_grid[i][j] = '.';
        }
        return false;
    }
public:
    void solveSudoku(vector<vector<char>> &grid) {
        vector<vector<char>> cpy_grid(grid);
        solve_grid(cpy_grid, grid, 0, 0);
    }
};
```

### n queens:
Problem Link: https://leetcode.com/problems/n-queens

#### - Python Solution
```python
class Solution:
    def solveNQueens(self, n: int) -> List[List[str]]:
        def backtrack(r):
            if r == n:
                curr_board = ["".join(row) for row in board]
                res.append(curr_board)
                return
            for c in range(n):
                if c in col or (r+c) in pos_diag or (r-c) in neg_diag:
                    continue
                col.add(c)
                pos_diag.add(r+c)
                neg_diag.add(r-c)
                board[r][c] = 'Q'
                backtrack(r+1)
                col.remove(c)
                pos_diag.remove(r+c)
                neg_diag.remove(r-c)
                board[r][c] = '.'

        col = set()
        pos_diag = set()
        neg_diag = set()
        res = []
        board = [['.' for j in range(n)] for i in range(n)]
        backtrack(0)
        return res
```
#### - CPP Solution
```cpp
class Solution {
    set<int> col;
    set<int> pos_diag;
    set<int> neg_diag;

    void backtrack(int r, int n, vector<string> &board, vector<vector<string>> &res) {
        if (r == n) {
            vector<string> curr_board(board);
            res.push_back(curr_board);
            return;
        }
        for (int c=0; c<n; c++) {
            if (col.find(c) != col.end() or
                pos_diag.find(r+c) != pos_diag.end() or
                neg_diag.find(r-c) != neg_diag.end())
                continue;
            col.insert(c);
            pos_diag.insert(r+c);
            neg_diag.insert(r-c);
            board[r][c] = 'Q';
            backtrack(r+1, n, board, res);
            col.erase(col.find(c));
            pos_diag.erase(pos_diag.find(r+c));
            neg_diag.erase(neg_diag.find(r-c));
            board[r][c] = '.';
        }
    }
public:
    vector<vector<string>> solveNQueens(int n) {
        vector<vector<string>> res;
        vector<string> board(n, string(n, '.'));
        backtrack(0, n, board, res);
        return res;
    }
};
```

### reverse nodes in k group:
Problem Link: https://leetcode.com/problems/reverse-nodes-in-k-group

#### - Python Solution
```python
class Solution:
    def reverseKGroup(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:
        def reverseList(head, tail):
            if head == None:
                return head
            prv = None
            cur = head
            nxt = cur.next
            while nxt != tail:
                cur.next = prv
                prv = cur
                cur = nxt
                nxt = nxt.next
            cur.next = prv
            return cur

        i = 0
        res = ListNode(0, head)
        curr_tail = res.next
        curr_head = res
        last_head = res.next
        while curr_tail:
            i += 1
            curr_tail = curr_tail.next
            if i % k == 0:
                curr_head.next = reverseList(curr_head.next, curr_tail)
                last_head.next = curr_tail
                curr_head = last_head
                last_head = curr_tail
        return res.next
```
#### - CPP Solution
```cpp
class Solution {
     ListNode* reverseList(ListNode *head, ListNode *tail) {
            if (head == NULL)
                return head;
            ListNode *prv = NULL;
            ListNode *cur = head;
            ListNode *nxt = cur->next;
            while (nxt != tail) {
                cur->next = prv;
                prv = cur;
                cur = nxt;
                nxt = nxt->next;
            }
            cur->next = prv;
            return cur;
     }
public:
    ListNode* reverseKGroup(ListNode *head, int k) {
        int i = 0;
        ListNode *res = new ListNode(0, head);
        ListNode *curr_tail = res->next;
        ListNode *curr_head = res;
        ListNode *last_head = res->next;
        while (curr_tail) {
            i ++;
            curr_tail = curr_tail->next;
            if (i % k == 0) {
                curr_head->next = reverseList(curr_head->next, curr_tail);
                last_head->next = curr_tail;
                curr_head = last_head;
                last_head = curr_tail;
            }
        }
        return res->next;
    }
};
```

### merge k sorted lists:
Problem Link: https://leetcode.com/problems/merge-k-sorted-lists

#### - Python Solution
```python
class Solution:
    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        def mergeTwoLists(list1, list2):
            head = ListNode()
            curr = head
            while list1 and list2:
                if list1.val <= list2.val:
                    curr.next = list1
                    list1 = list1.next
                else:
                    curr.next = list2
                    list2 = list2.next
                curr = curr.next
            if list1:
                curr.next = list1
            if list2:
                curr.next = list2
            return head.next

        if len(lists) == 0:
            return None
        for i in range(1, len(lists)):
            lists[0] = mergeTwoLists(lists[0], lists[i])
        return lists[0]
```
#### - CPP Solution
```cpp
class Solution {
    ListNode* mergeTwoLists(ListNode *list1, ListNode *list2) {
        ListNode *head = new ListNode();
        ListNode *curr = head;
        while (list1 and list2) {
            if (list1->val <= list2->val)
                curr->next = list1,
                list1 = list1->next;
            else
                curr->next = list2,
                list2 = list2->next;
            curr = curr->next;
        }
        if (list1)
            curr->next = list1;
        if (list2)
            curr->next = list2;
        return head->next;
    }
public:
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        if (size(lists) == 0)
            return NULL;
        for (int i=1; i<size(lists); i++)
            lists[0] = mergeTwoLists(lists[0], lists[i]);
        return lists[0];
    }
};
```

### smallest range covering elements from k lists:
Problem Link: https://leetcode.com/problems/smallest-range-covering-elements-from-k-lists

#### - Python Solution
```python
import queue

class Solution:
    def smallestRange(self, nums: List[List[int]]) -> List[int]:
        min_heap = queue.PriorityQueue()
        max_end = -2e5
        for i in range(len(nums)):
            min_heap.put((nums[i][0], i, 0))
            max_end = max(max_end, nums[i][0])
        t, i, j = min_heap.get()
        res = [t, max_end]
        while j < len(nums[i])-1:
            max_end = max(max_end, nums[i][j+1])
            min_heap.put((nums[i][j+1], i, j+1))
            t, i, j = min_heap.get()
            if max_end - t < res[1] - res[0]:
                res[0], res[1] = t, max_end
        return res
```
#### - CPP Solution
```cpp
class Solution {
    struct Item {
        int t, i, j;
        Item(int t, int i, int j) :
            t(t), i(i), j(j) {
        }
    };
public:
    vector<int> smallestRange(vector<vector<int>> &nums) {
        auto comp = [](const Item &x, const Item &y) {
            return x.t > y.t;
        };
        priority_queue<Item, vector<Item>, decltype(comp)> min_heap(comp);
        int max_end = -2e5;
        for (int i=0; i<size(nums); i++) {
            min_heap.push(Item(nums[i][0], i, 0));
            max_end = max(max_end, nums[i][0]);
        }
        Item x = min_heap.top();
        min_heap.pop();
        vector<int> res = {x.t, max_end};
        while (x.j < size(nums[x.i])-1) {
            max_end = max(max_end, nums[x.i][x.j+1]);
            min_heap.push(Item(nums[x.i][x.j+1], x.i, x.j+1));
            x = min_heap.top();
            min_heap.pop();
            if (max_end - x.t < res[1] - res[0])
                res[0] = x.t, res[1] = max_end;
        }
        return res;
    }
};
```

### employee free time:
Problem Link: https://leetcode.com/problems/employee-free-time

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### count of range sum:
Problem Link: https://leetcode.com/problems/count-of-range-sum

#### - Python Solution
```python
class Solution:
    def countRangeSum(self, nums: List[int], lower: int, upper: int) -> int:
        def merge_sort(l, r):
            m = (l+r) // 2
            if l == m:
                return 0
            res = merge_sort(l, m) + merge_sort(m, r)
            i, j = m, m
            for k in range(l, m):
                while i < r and cumulative_sum[i] - cumulative_sum[k] <  lower:
                    i += 1
                while j < r and cumulative_sum[j] - cumulative_sum[k] <= upper:
                    j += 1
                res += j - i
            cumulative_sum[l:r] = sorted(cumulative_sum[l:r])
            return res

        cumulative_sum = [0] * (len(nums)+1)
        for i in range(len(nums)):
            cumulative_sum[i+1] = cumulative_sum[i] + nums[i]
        return merge_sort(0, len(cumulative_sum))
```
#### - CPP Solution
```cpp
class Solution {
    int merge_sort(int l, int r, vector<long> &cumulative_sum, int lower, int upper) {
        int m = (l+r) / 2;
        if (l == m)
            return 0;
        int res = merge_sort(l, m, cumulative_sum, lower, upper) +
                  merge_sort(m, r, cumulative_sum, lower, upper);
        int i = m, j = m;
        for (int k=l; k<m; k++) {
            while (i < r and cumulative_sum[i] - cumulative_sum[k] <  lower)
                i ++;
            while (j < r and cumulative_sum[j] - cumulative_sum[k] <= upper)
                j ++;
            res += j - i;
        }
        sort(cumulative_sum.begin()+l, cumulative_sum.begin()+r);
        return res;
    }
public:
    int countRangeSum(vector<int> &nums, int lower, int upper) {
        vector<long> cumulative_sum(size(nums)+1, 0);
        for (int i=0; i<size(nums); i++)
            cumulative_sum[i+1] = cumulative_sum[i] + nums[i];
        return merge_sort(0, size(cumulative_sum), cumulative_sum, lower, upper);
    }
};
```

### sliding window maximum:
Problem Link: https://leetcode.com/problems/sliding-window-maximum

#### - Python Solution
```python
class Solution:
    def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:
        q = deque()
        res = []
        for i in range(len(nums)):
            while q and nums[i] > q[-1][0]:
                q.pop()
            q.append((nums[i], i))
            if i < k-1:
                continue
            res.append(q[0][0])
            if i - q[0][1] + 1 == k:
                q.popleft()
        return res
```
#### - CPP Solution
```cpp
class Solution {
public:
    vector<int> maxSlidingWindow(vector<int> &nums, int k) {
        deque<pair<int, int>> q;
        vector<int> res;
        for (int i=0; i<size(nums); i++) {
            while (size(q) and nums[i] > q.back().first)
                q.pop_back();
            q.push_back({nums[i], i});
            if (i < k-1)
                continue;
            res.push_back(q[0].first);
            if (i - q.front().second + 1 == k)
                q.pop_front();
        }
        return res;
    }
};
```

### minimum number of k consecutive bit flips:
Problem Link: https://leetcode.com/problems/minimum-number-of-k-consecutive-bit-flips

#### - Python Solution
```python
class Solution:
    def minKBitFlips(self, nums: List[int], k: int) -> int:
        res, flipped = 0, 0
        is_flipped = [0] * len(nums)
        for i in range(len(nums)):
            if i >= k:
                flipped ^= is_flipped[i-k]
            if flipped != nums[i]:
                continue
            if i+k > len(nums):
                return -1
            is_flipped[i] = 1
            flipped = 1 - flipped
            res += 1
        return res
```
#### - CPP Solution
```cpp
class Solution {
public:
    int minKBitFlips(vector<int> &nums, int k) {
        int res = 0, flipped = 0;
        vector<int> is_flipped(size(nums), 0);
        for (int i=0; i<size(nums); i++) {
            if (i >= k)
                flipped ^= is_flipped[i-k];
            if (flipped != nums[i])
                continue;
            if (i+k > size(nums))
                return -1;
            is_flipped[i] = 1;
            flipped = 1 - flipped;
            res ++;
        }
        return res;
    }
};
```

### count unique characters of all substrings of a given string:
Problem Link:

#### - Python Solution
```python
class Solution:
    def uniqueLetterString(self, s: str) -> int:
        idx = {chr(i): [-1, -1] for i in range(ord('A'), ord('Z')+1)}
        res = 0
        for i in range(len(s)):
            k, j = idx[s[i]]
            res += (i-j) * (j-k)
            idx[s[i]] = [j, i]
        for i in idx:
            k, j = idx[i]
            res += (len(s)-j) * (j-k)
        return res
```
#### - CPP Solution
```cpp
class Solution {
public:
    int uniqueLetterString(string s) {
        map<char, pair<int, int>> idx;
        for (char i='A'; i<='Z'; i++)
            idx[i] = {-1, -1};
        int res = 0;
        for (int i=0; i<size(s); i++) {
            auto [k, j] = idx[s[i]];
            res += (i-j) * (j-k);
            idx[s[i]] = {j, i};
        }
        for (auto &[i, v] : idx) {
            auto [k, j] = v;
            res += (size(s)-j) * (j-k);
        }
        return res;
    }
};
```

### minimum window substring:
Problem Link: https://leetcode.com/problems/minimum-window-substring

#### - Python Solution
```python
class Solution:
    def minWindow(self, s: str, t: str) -> str:
        cnt, window = {}, {}
        for i in t:
            cnt[i] = cnt.get(i, 0) + 1
        curr, need = 0, len(cnt)
        res_i, res_j, res_len = -1, -1, 2e5
        j = 0
        for i in range(len(s)):
            window[s[i]] = window.get(s[i], 0) + 1
            if s[i] in cnt and window[s[i]] == cnt[s[i]]:
                curr += 1
            while curr == need:
                if i-j+1 < res_len:
                    res_i, res_j, res_len = j, i, i-j+1
                window[s[j]] -= 1
                if s[j] in cnt and window[s[j]] < cnt[s[j]]:
                    curr -= 1
                j += 1
        return s[res_i:res_j+1] if res_len != 2e5 else ""
```
#### - CPP Solution
```cpp
class Solution {
public:
    string minWindow(string s, string t) {
        map<char, int> cnt, window;
        for (char i : t)
            cnt[i] ++;
        int curr = 0, need = size(cnt);
        int res_i = -1, res_j = -1, res_len = 2e5;
        int j = 0;
        for (int i=0; i<size(s); i++) {
            window[s[i]] ++;
            if (cnt.find(s[i]) != cnt.end() and window[s[i]] == cnt[s[i]])
                curr ++;
            while (curr == need) {
                if (i-j+1 < res_len)
                    res_i = j, res_j = i, res_len = i-j+1;
                window[s[j]] --;
                if (cnt.find(s[j]) != cnt.end() and window[s[j]] < cnt[s[j]])
                    curr --;
                j ++;
            }
        }
        return res_len != 2e5? s.substr(res_i, res_j-res_i+1) : "";
    }
};
```

### substring with concatenation of all words:
Problem Link: https://leetcode.com/problems/substring-with-concatenation-of-all-words

#### - Python Solution
```python
class Solution:
    def findSubstring(self, s: str, words: List[str]) -> List[int]:
        cnt, sub = {}, {}
        res = []
        is_substr = True
        n = len(words[0])
        if len(s) <= 0 or len(s) < len(words)*n:
            return res
        for i in range(len(words)):
            cnt[words[i]] = cnt.get(words[i], 0) + 1
        for i in range(len(s)-n*len(words)+1):
            is_substr = True
            sub.clear()
            if s[i:i+n] not in cnt:
                continue
            for j in range(len(words)):
                next_word = s[i+j*n:i+j*n+n]
                if next_word in cnt:
                    sub[next_word] = sub.get(next_word, 0) + 1
                if next_word not in cnt or \
                    sub[next_word] > cnt[next_word]:
                    is_substr = False
                    break
            if is_substr == True:
                res.append(i)
        return res
```
#### - CPP Solution
```cpp
class Solution {
public:
    vector<int> findSubstring(string s, vector<string> &words) {
        map<string, int> cnt;
        map<string, int> sub;
        vector<int> res;
        bool is_substr = true;
        int n = size(words[0]);
        if (size(s) <= 0 or size(s) < size(words)*n)
            return res;
        for (int i=0; i<size(words); i++)
            cnt[words[i]] ++;
        for (int i=0; i<size(s)-n*size(words)+1; i++) {
            is_substr = true;
            sub.clear();
            if (cnt.find(s.substr(i, n)) == cnt.end())
                continue;
            for (int j=0 ; j<size(words); j++){
                string next_word = s.substr(i+j*n, n);
                if (cnt.find(next_word) != cnt.end())
                    sub[next_word] ++;
                if (cnt.find(next_word) == cnt.end() or
                    sub[next_word] > cnt[next_word]) {
                    is_substr = false;
                    break;
                }
            }
            if (is_substr == true)
                res.push_back(i);
        }
        return res;
    }
};
```

### rearrange string k distance apart:
Problem Link: https://leetcode.com/problems/rearrange-string-k-distance-apart

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### course schedule iii:
Problem Link: https://leetcode.com/problems/course-schedule-iii

#### - Python Solution
```python
import queue

class Solution:
    def scheduleCourse(self, courses: List[List[int]]) -> int:
        courses.sort(key = lambda x: x[1])
        max_heap = queue.PriorityQueue()
        now = 0
        for t, end in courses:
            now += t
            max_heap.put(-t)
            if now > end:
                now += max_heap.get()
        return max_heap.qsize()
```
#### - CPP Solution
```cpp
class Solution {
public:
    int scheduleCourse(vector<vector<int>> &courses) {
        sort(courses.begin(), courses.end(), [](const vector<int> &x, const vector<int> &y) {
                                                return x[1] < y[1];}
            );
        priority_queue<int> max_heap;
        int now = 0;
        for (auto it : courses) {
            now += it[0];
            max_heap.push(it[0]);
            if (now > it[1]) {
                now += -max_heap.top();
                max_heap.pop();
            }
        }
        return size(max_heap);
    }
};
```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname:
Problem Link:

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```
