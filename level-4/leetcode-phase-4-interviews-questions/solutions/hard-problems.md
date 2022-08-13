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
