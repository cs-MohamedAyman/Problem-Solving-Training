<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="80" src="/logos/leetcode.png"></img></a>

# LeetCode OJ - Interviews Questions <br> Medium Problems II `35 problems`

## partition equal subset sum
Problem Link: https://leetcode.com/problems/partition-equal-subset-sum

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def canPartition(self, nums: List[int]) -> bool:
        nums_sum = sum(nums)
        if nums_sum % 2:
            return False
        all_sums = set([0])
        half = nums_sum // 2
        for i in nums:
            prev_all_sums = all_sums.copy()
            for j in prev_all_sums:
                all_sums.add(j+i)
            if half in all_sums:
                return True
        return False
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    bool canPartition(vector<int> &nums) {
        int nums_sum = accumulate(nums.begin(), nums.end(), 0);
        if (nums_sum % 2)
            return false;
        set<int> all_sums = {0};
        int half = nums_sum / 2;
        for (int i : nums) {
            set<int> prev_all_sums(all_sums.begin(), all_sums.end());
            for (int j : prev_all_sums)
                all_sums.insert(j+i);
            if (all_sums.find(half) != all_sums.end())
                return true;
        }
        return false;
    }
};
```

</details>

## partition to k equal sum subsets
Problem Link: https://leetcode.com/problems/partition-to-k-equal-sum-subsets

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def canPartitionKSubsets(self, nums: List[int], k: int) -> bool:
        def check_partitions(i, k, curr_total):
            if k == 0:
                return True
            if curr_total > target:
                return False
            if curr_total == target:
                return check_partitions(0, k-1, 0)
            for j in range(i, len(nums)):
                if visited[j]:
                    continue
                visited[j] = True
                if check_partitions(j+1, k, curr_total+nums[j]):
                    return True
                visited[j] = False
            return False

        nums_sum = sum(nums)
        if nums_sum % k:
            return False
        target = nums_sum // k
        nums.sort(reverse=True)
        visited = [0] * len(nums)
        return check_partitions(0, k, 0)
```
`TODO` TIME-LIMIT-EXCEEDED


</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    bool check_partitions(int i, int k, int curr_total,
                          const int &target, const vector<int> &nums, bool visited[]) {
        if (k == 0)
            return true;
        if (curr_total > target)
            return false;
        if (curr_total == target)
            return check_partitions(0, k-1, 0, target, nums, visited);
        for (int j=i; j<size(nums); j++) {
            if (visited[j])
                continue;
            visited[j] = true;
            if (check_partitions(j+1, k, curr_total+nums[j], target, nums, visited))
                return true;
            visited[j] = false;
        }
        return false;
    }
public:
    bool canPartitionKSubsets(vector<int> &nums, int k) {
        int nums_sum = accumulate(nums.begin(), nums.end(), 0);
        if (nums_sum % k)
            return false;
        int target = nums_sum / k;
        sort(nums.rbegin(), nums.rend());
        bool visited[16] = {0};
        return check_partitions(0, k, 0, target, nums, visited);
    }
};
```
`TODO` TIME-LIMIT-EXCEEDED

</details>

## best time to buy and sell stock with cooldown
Problem Link: https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        def dp(i, buy):
            if i >= len(prices):
                return 0
            if memo[i][buy] != -1:
                return memo[i][buy]
            cooldown = dp(i+1, buy)
            if buy:
                memo[i][buy] = max(dp(i+1, 1-buy) - prices[i], cooldown)
            else:
                memo[i][buy] = max(dp(i+2, 1-buy) + prices[i], cooldown)
            return memo[i][buy]

        memo = [[-1 for i in range(2)] for j in range(5003)]
        return dp(0, 1)
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    int memo[5003][2];
    int dp(int i, bool buy, const vector<int> &prices) {
        if (i >= size(prices))
            return 0;
        if (memo[i][buy] != -1)
            return memo[i][buy];
        int cooldown = dp(i+1, buy, prices);
        if (buy)
            memo[i][buy] = max(dp(i+1, 1-buy, prices) - prices[i], cooldown);
        else
            memo[i][buy] = max(dp(i+2, 1-buy, prices) + prices[i], cooldown);
        return memo[i][buy];
    }
public:
    int maxProfit(vector<int> &prices) {
        memset(memo, -1, sizeof memo);
        return dp(0, 1, prices);
    }
};
```

</details>

## linked list cycle ii
Problem Link: https://leetcode.com/problems/linked-list-cycle-ii

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if not head:
            return
        curr1 = head
        curr2 = head
        while curr2 and curr2.next:
            curr2 = curr2.next.next
            curr1 = curr1.next
            if curr1 == curr2:
                break
        if not curr2 or not curr2.next:
            return
        curr2 = head
        while curr1 and curr2:
            if curr1 == curr2:
                return curr1
            curr1 = curr1.next
            curr2 = curr2.next
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    ListNode* detectCycle(ListNode *head) {
        if (not head)
            return NULL;
        ListNode *curr1 = head;
        ListNode *curr2 = head;
        while (curr2 and curr2->next) {
            curr2 = curr2->next->next;
            curr1 = curr1->next;
            if (curr1 == curr2)
                break;
        }
        if (not curr2 or not curr2->next)
            return NULL;
        curr2 = head;
        while (curr1 and curr2) {
            if (curr1 == curr2)
                return curr1;
            curr1 = curr1->next;
            curr2 = curr2->next;
        }
        return NULL;
    }
};
```

</details>

## add two numbers
Problem Link: https://leetcode.com/problems/add-two-numbers

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        cry = 0
        head = ListNode()
        curr = head
        while l1 or l2 or cry:
            cry += (l1.val if l1 else 0) + (l2.val if l2 else 0)
            curr.next = ListNode(cry % 10)
            cry //= 10
            curr = curr.next
            l1 = l1.next if l1 else None
            l2 = l2.next if l2 else None
        return head.next
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    ListNode* addTwoNumbers(ListNode *l1, ListNode *l2) {
        int cry = 0;
        ListNode *head = new ListNode();
        ListNode *curr = head;
        while (l1 or l2 or cry) {
            cry += (l1? l1->val : 0) + (l2? l2->val : 0);
            curr->next = new ListNode(cry % 10);
            cry /= 10;
            curr = curr->next;
            l1 = l1? l1->next : NULL;
            l2 = l2? l2->next : NULL;
        }
        return head->next;
    }
};
```

</details>

## remove nth node from end of list
Problem Link: https://leetcode.com/problems/remove-nth-node-from-end-of-list

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        res = ListNode(0, head)
        curr1 = res
        curr2 = head
        while n:
            curr2 = curr2.next
            n -= 1
        while curr2:
            curr1 = curr1.next
            curr2 = curr2.next
        curr1.next = curr1.next.next
        return res.next
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode *head, int n) {
        ListNode *res = new ListNode(0, head);
        ListNode *curr1 = res;
        ListNode *curr2 = head;
        while (n) {
            curr2 = curr2->next;
            n --;
        }
        while (curr2) {
            curr1 = curr1->next;
            curr2 = curr2->next;
        }
        curr1->next = curr1->next->next;
        return res->next;
    }
};
```

</details>

## sort list
Problem Link: https://leetcode.com/problems/sort-list

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def sortList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        def beforeMiddleNode(head):
            curr1 = head
            curr2 = head.next
            while curr2 and curr2.next:
                curr2 = curr2.next.next
                curr1 = curr1.next
            return curr1

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

        def merge_sort(head):
            if not head or not head.next:
                return head
            left = head
            right = beforeMiddleNode(head)
            temp = right.next
            right.next = None
            right = temp
            left  = merge_sort(left)
            right = merge_sort(right)
            return mergeTwoLists(left, right)

        return merge_sort(head)
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    ListNode* beforeMiddleNode(ListNode *head) {
        ListNode *curr1 = head;
        ListNode *curr2 = head->next;
        while (curr2 and curr2->next) {
            curr2 = curr2->next->next;
            curr1 = curr1->next;
        }
        return curr1;
    }
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
    ListNode* merge_sort(ListNode *head) {
            if (not head or not head->next)
                return head;
            ListNode *left  = head;
            ListNode *right = beforeMiddleNode(head);
            ListNode *temp  = right->next;
            right->next = NULL;
            right = temp;
            left  = merge_sort(left);
            right = merge_sort(right);
            return mergeTwoLists(left, right);
    }
public:
    ListNode* sortList(ListNode *head) {
        return merge_sort(head);
    }
};
```

</details>

## reorder list
Problem Link: https://leetcode.com/problems/reorder-list

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def reorderList(self, head: Optional[ListNode]) -> None:
        def beforeMiddleNode(head):
            curr1 = head
            curr2 = None
            if head.next:
                curr2 = head.next.next
            while curr2 and curr2.next:
                curr2 = curr2.next.next
                curr1 = curr1.next
            return curr1

        def reverseList(head):
            if head == None:
                return head
            prv = None
            cur = head
            nxt = cur.next
            while nxt:
                cur.next = prv
                prv = cur
                cur = nxt
                nxt = nxt.next
            cur.next = prv
            return cur

        def mergeTwoLists(list1, list2):
            head = ListNode()
            curr = head
            while list1 and list2:
                curr.next = list1
                list1 = list1.next
                curr = curr.next
                curr.next = list2
                list2 = list2.next
                curr = curr.next
            return head.next

        mid = beforeMiddleNode(head)
        temp = mid.next
        mid.next = None
        mid = temp
        mid = reverseList(mid)
        head = mergeTwoLists(head, mid)
        return head
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    ListNode* beforeMiddleNode(ListNode *head) {
        ListNode *curr1 = head;
        ListNode *curr2 = NULL;
        if (head->next)
            curr2 = head->next->next;
        while (curr2 and curr2->next) {
            curr2 = curr2->next->next;
            curr1 = curr1->next;
        }
        return curr1;
    }
    ListNode* reverseList(ListNode *head) {
        if (head == NULL)
            return head;
        ListNode *prv = NULL;
        ListNode *cur = head;
        ListNode *nxt = cur->next;
        while (nxt) {
            cur->next = prv;
            prv = cur;
            cur = nxt;
            nxt = nxt->next;
        }
        cur->next = prv;
        return cur;
    }
    ListNode* mergeTwoLists(ListNode *list1, ListNode *list2) {
        ListNode *head = new ListNode();
        ListNode *curr = head;
        while (list1 and list2) {
            curr->next = list1,
            list1 = list1->next;
            curr = curr->next;
            curr->next = list2,
            list2 = list2->next;
            curr = curr->next;
        }
        return head->next;
    }
public:
    void reorderList(ListNode *head) {
        ListNode *mid = beforeMiddleNode(head);
        ListNode *temp = mid->next;
        mid->next = NULL;
        mid = temp;
        mid = reverseList(mid);
        head = mergeTwoLists(head, mid);
    }
};
```

</details>

## clone graph
Problem Link: https://leetcode.com/problems/clone-graph

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def cloneGraph(self, node: 'Node') -> 'Node':
        def dfs(u):
            if u in adj:
                return adj[u]
            new_u = Node(u.val)
            adj[u] = new_u
            for v in u.neighbors:
                new_u.neighbors.append(dfs(v))
            return new_u

        adj = {}
        return dfs(node) if node else None
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    map<Node*, Node*> adj;

    Node* dfs(Node *u) {
        if (adj.find(u) != adj.end())
            return adj[u];
        Node *new_u = new Node(u->val);
        adj[u] = new_u;
        for (Node *v : u->neighbors)
            new_u->neighbors.push_back(dfs(v));
        return new_u;
    }
public:
    Node* cloneGraph(Node* node) {
        return node? dfs(node) : NULL;
    }
};
```

</details>

## pacific atlantic water flow
Problem Link: https://leetcode.com/problems/pacific-atlantic-water-flow

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def pacificAtlantic(self, heights: List[List[int]]) -> List[List[int]]:
        def dfs(r, c, visited, prev_h):
            if (r, c) in visited or not(0 <= r < n) or not(0 <= c < m) or heights[r][c] < prev_h:
                return
            visited.add((r, c))
            for i in range(4):
                dfs(r+dx[i], c+dy[i], visited, heights[r][c])

        n, m = len(heights), len(heights[0])
        visited1, visited2 = set(), set()
        dx = [0, 0, 1, -1]
        dy = [-1, 1, 0, 0]
        for c in range(m):
            dfs(0,   c, visited1, heights[0][c])
            dfs(n-1, c, visited2, heights[n-1][c])
        for r in range(n):
            dfs(r, 0,   visited1, heights[r][0])
            dfs(r, m-1, visited2, heights[r][m-1])
        res = list(visited1 & visited2)
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    set<pair<int, int>> visited1, visited2;
    int dx[] = {0, 0, 1, -1};
    int dy[] = {-1, 1, 0, 0};

    void dfs(int r, int c, set<pair<int, int>> &visited, int prev_h,
             const vector<vector<int>> &heights, int n, int m) {
        if (visited.find({r, c}) != visited.end() or
            not(0 <= r and r < n) or not(0 <= c and c < m) or heights[r][c] < prev_h)
            return;
        visited.insert({r, c});
        for (int i=0; i<4; i++)
            dfs(r+dx[i], c+dy[i], visited, heights[r][c], heights, n, m);
    }
public:
    vector<vector<int>> pacificAtlantic(vector<vector<int>> &heights) {
        int n = size(heights), m = size(heights[0]);
        for (int c=0; c<m; c++) {
            dfs(0,   c, visited1, heights[0][c], heights, n, m);
            dfs(n-1, c, visited2, heights[n-1][c], heights, n, m);
        }
        for (int r=0; r<n; r++) {
            dfs(r, 0,   visited1, heights[r][0], heights, n, m);
            dfs(r, m-1, visited2, heights[r][m-1], heights, n, m);
        }
        vector<pair<int, int>> res;
        set_intersection(visited1.begin(), visited1.end(), visited2.begin(), visited2.end(),
                         back_inserter(res));
        vector<vector<int>> ans;
        for (auto &[i, j] : res)
            ans.push_back({i, j});
        return ans;
    }
};
```

</details>

## number of islands
Problem Link: https://leetcode.com/problems/number-of-islands

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        def dfs(r, c):
            if (r, c) in visit or not(0 <= r < n) or not(0 <= c < m) or grid[r][c] == '0':
                return
            visit.add((r, c))
            for i in range(4):
                dfs(r+dx[i], c+dy[i])

        n, m = len(grid), len(grid[0])
        visit = set()
        dx = [0, 0, 1, -1]
        dy = [-1, 1, 0, 0]
        res = 0
        for r in range(n):
            for c in range(m):
                if grid[r][c] == '1' and (r, c) not in visit:
                    dfs(r, c)
                    res += 1
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    set<pair<int, int>> visited;
    int dx[4] = {0, 0, 1, -1};
    int dy[4] = {-1, 1, 0, 0};

    void dfs(int r, int c, const vector<vector<char>> &grid, int n, int m) {
        if (visited.find({r, c}) != visited.end() or
            not(0 <= r and r < n) or not(0 <= c and c < m) or grid[r][c] == '0')
            return;
        visited.insert({r, c});
        for (int i=0; i<4; i++)
            dfs(r+dx[i], c+dy[i], grid, n, m);
    }
public:
    int numIslands(vector<vector<char>> &grid) {
        int n = size(grid), m = size(grid[0]);
        int res = 0;
        for (int r=0; r<n; r++) {
            for (int c=0; c<m; c++) {
                if (grid[r][c] == '1' and visited.find({r, c}) == visited.end()) {
                    dfs(r, c, grid, n, m);
                    res ++;
                }
            }
        }
        return res;
    }
};
```

</details>

## graph valid tree
Problem Link: https://leetcode.com/problems/graph-valid-tree

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## number of connected components in an undirected graph
Problem Link: https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## reverse linked list ii
Problem Link: https://leetcode.com/problems/reverse-linked-list-ii

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def reverseBetween(self, head: Optional[ListNode], left: int, right: int) -> Optional[ListNode]:
        res = ListNode(0, head)
        prev_left, cur = res, head
        for i in range(left-1):
            prev_left = cur
            cur = cur.next
        prv = None
        for i in range(right-left+1):
            tmp = cur.next
            cur.next = prv
            prv = cur
            cur = tmp
        prev_left.next.next = cur
        prev_left.next = prv
        return res.next
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    ListNode* reverseBetween(ListNode *head, int left, int right) {
        ListNode *res = new ListNode(0, head);
        ListNode *prev_left = res, *cur = head;
        for (int i=0; i<left-1; i++) {
            prev_left = cur;
            cur = cur->next;
        }
        ListNode *prv = NULL;
        for (int i=0; i<right-left+1; i++) {
            ListNode *tmp = cur->next;
            cur->next = prv;
            prv = cur;
            cur = tmp;
        }
        prev_left->next->next = cur;
        prev_left->next = prv;
        return res->next;
    }
};
```

</details>

## rotate list
Problem Link: https://leetcode.com/problems/rotate-list

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def rotateRight(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:
        def get_length(curr):
            res = 0
            while curr:
                curr = curr.next
                res += 1
            return res

        if not head or not head.next:
            return head
        k %= get_length(head)
        if k == 0:
            return head
        res = ListNode(0, head)
        curr1 = res
        curr2 = head
        while k:
            curr2 = curr2.next
            k -= 1
        while curr2.next:
            curr1 = curr1.next
            curr2 = curr2.next
        curr1 = curr1.next
        new_head = curr1.next
        curr1.next = None
        curr2.next = head
        res.next = new_head
        return res.next
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    int get_length(ListNode *curr) {
        int res = 0;
        while (curr) {
            curr = curr->next;
            res ++;
        }
        return res;
    }
public:
    ListNode* rotateRight(ListNode *head, int k) {
        if (not head or not head->next)
            return head;
        k %= get_length(head);
        if (k == 0)
            return head;
        ListNode *res = new ListNode(0, head);
        ListNode *curr1 = res;
        ListNode *curr2 = head;
        while (k) {
            curr2 = curr2->next;
            k --;
        }
        while (curr2->next) {
            curr1 = curr1->next;
            curr2 = curr2->next;
        }
        curr1 = curr1->next;
        ListNode *new_head = curr1->next;
        curr1->next = NULL;
        curr2->next = head;
        res->next = new_head;
        return res->next;
    }
};
```

</details>

## swap nodes in pairs
Problem Link: https://leetcode.com/problems/swap-nodes-in-pairs

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def swapPairs(self, head: Optional[ListNode]) -> Optional[ListNode]:
        res = ListNode(0, head)
        prev, curr = res, head
        while curr and curr.next:
            temp1 = curr.next.next
            temp2 = curr.next
            temp2.next = curr
            curr.next = temp1
            prev.next = temp2
            prev = curr
            curr = temp1
        return res.next
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    ListNode* swapPairs(ListNode *head) {
        ListNode *res = new ListNode(0, head);
        ListNode *prev = res, *curr = head;
        while (curr and curr->next) {
            ListNode *temp1 = curr->next->next;
            ListNode *temp2 = curr->next;
            temp2->next = curr;
            curr->next = temp1;
            prev->next = temp2;
            prev = curr;
            curr = temp1;
        }
        return res->next;
    }
};
```

</details>

## odd even linked list
Problem Link: https://leetcode.com/problems/odd-even-linked-list

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def oddEvenList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if not head:
            return head
        odd  = head
        even = head.next
        original_even = even
        while even and even.next:
            odd.next = even.next
            odd = odd.next
            even.next = odd.next
            even = even.next
        odd.next = original_even
        return head
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    ListNode* oddEvenList(ListNode *head) {
        if (not head)
            return head;
        ListNode *odd  = head;
        ListNode *even = head->next;
        ListNode *original_even = even;
        while (even and even->next) {
            odd->next = even->next;
            odd = odd->next;
            even->next = odd->next;
            even = even->next;
        }
        odd->next = original_even;
        return head;
    }
};
```

</details>

## kth smallest element in a sorted matrix
Problem Link: https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def kthSmallest(self, matrix: List[List[int]], k: int) -> int:
        def binary_search_upper(arr, x):
            l, r = 0, len(arr)-1
            while l <= r:
                m = (l+r) // 2
                if arr[m] <= x:
                    l = m+1
                else:
                    r = m-1
            return l

        def count_less_k(m):
            res = 0
            for i in range(n):
                res += binary_search_upper(matrix[i], m)
            return res

        l, r, n = matrix[0][0], matrix[-1][-1], len(matrix)
        while l <= r:
            m = (l+r) // 2
            if count_less_k(m) < k:
                l = m+1
            else:
                r = m-1
        return l
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    int n;

    int binary_search_upper(const vector<int> &arr, int x) {
        int l = 0, r = size(arr)-1;
        while (l <= r) {
            int m = (l+r) / 2;
            if (arr[m] <= x)
                l = m+1;
            else
                r = m-1;
        }
        return l;
    }
    int count_less_k(int m, const vector<vector<int>> &matrix) {
        int res = 0;
        for (int i=0; i<n; i++)
            res += binary_search_upper(matrix[i], m);
        return res;
    }
public:
    int kthSmallest(vector<vector<int>>& matrix, int k) {
        n = size(matrix);
        int l = matrix[0][0], r = matrix[n-1][n-1];
        while (l <= r) {
            int m = (l+r) / 2;
            if (count_less_k(m, matrix) < k)
                l = m+1;
            else
                r = m-1;
        }
        return l;
    }
};
```

</details>

## find k pairs with smallest sums
Problem Link: https://leetcode.com/problems/find-k-pairs-with-smallest-sums

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
import queue

class Solution:
    def kSmallestPairs(self, nums1: List[int], nums2: List[int], k: int) -> List[List[int]]:
        min_heap = queue.PriorityQueue()
        n, m = len(nums1), len(nums2)
        for i in range(min(n, k)):
            t = nums1[i] + nums2[0]
            n1, n2 = nums1[i], nums2[0]
            min_heap.put((t, n1, n2, 0))
        res = []
        while k and not min_heap.empty():
            t, n1, n2, idx = min_heap.get()
            res.append((n1 ,n2))
            k -= 1
            if idx < m-1:
                t = n1 + nums2[idx+1]
                n1, n2 = n1, nums2[idx+1]
                min_heap.put((t, n1 , n2, idx+1))
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    struct Item {
        int t, n1, n2, idx;
        Item(int t, int n1, int n2, int idx) :
            t(t), n1(n1), n2(n2), idx(idx) {
        }
    };
public:
    vector<vector<int>> kSmallestPairs(vector<int> &nums1, vector<int> &nums2, int k) {
        auto comp = [](const Item &x, const Item &y) { return x.t > y.t; };
        priority_queue<Item, vector<Item>, decltype(comp)> min_heap(comp);
        int n = size(nums1), m = size(nums2);
        for (int i=0; i<min(n, k); i++) {
            int n1 = nums1[i], n2 = nums2[0];
            min_heap.push(Item(n1+n2, n1, n2, 0));
        }
        vector<vector<int>> res;
        while (k and not min_heap.empty()) {
            Item x = min_heap.top();
            res.push_back({x.n1, x.n2});
            min_heap.pop();
            k --;
            if (x.idx < m-1) {
                int n1 = x.n1, n2 = nums2[x.idx+1];
                min_heap.push(Item(n1+n2, n1, n2, x.idx+1));
            }
        }
        return res;
    }
};
```

</details>

## merge intervals
Problem Link: https://leetcode.com/problems/merge-intervals

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        intervals.sort()
        res = [intervals[0]]
        for s, e in intervals:
            if s <= res[-1][1]:
                res[-1][1] = max(res[-1][1], e)
            else:
                res.append([s, e])
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<vector<int>> merge(vector<vector<int>> &intervals) {
        sort(intervals.begin(), intervals.end());
        vector<vector<int>> res;
        res.push_back(intervals[0]);
        for (auto &it : intervals) {
            int s = it[0], e = it[1];
            if (s <= res[size(res)-1][1])
                res[size(res)-1][1] = max(res[size(res)-1][1], e);
            else
                res.push_back({s, e});
        }
        return res;
    }
};
```

</details>

## Interval List Intersections
Problem Link: https://leetcode.com/problems/interval-list-intersections

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def intervalIntersection(self, firstList: List[List[int]], secondList: List[List[int]]) -> List[List[int]]:
        i, j = 0, 0
        n, m = len(firstList), len(secondList)
        res = []
        while i < n and j < m:
            lo = max(firstList[i][0], secondList[j][0])
            hi = min(firstList[i][1], secondList[j][1])
            if lo <= hi:
                res.append((lo, hi))
            if firstList[i][1] > secondList[j][1]:
                j += 1
            else:
                i += 1
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<vector<int>> intervalIntersection(vector<vector<int>> &firstList, vector<vector<int>> &secondList) {
        int i = 0, j = 0;
        int n = size(firstList), m = size(secondList);
        vector<vector<int>> res;
        while (i < n and j < m) {
            int lo = max(firstList[i][0], secondList[j][0]);
            int hi = min(firstList[i][1], secondList[j][1]);
            if (lo <= hi)
                res.push_back({lo, hi});
            if (firstList[i][1] > secondList[j][1])
                j ++;
            else
                i ++;
        }
        return res;
    }
};
```

</details>

## non overlapping intervals
Problem Link: https://leetcode.com/problems/non-overlapping-intervals

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def eraseOverlapIntervals(self, intervals: List[List[int]]) -> int:
        intervals.sort()
        res = 0
        prev_end = -int(5e4)
        for s, e in intervals:
            if s >= prev_end:
                prev_end = e
            else:
                res += 1
                prev_end = min(e, prev_end)
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int eraseOverlapIntervals(vector<vector<int>> &intervals) {
        sort(intervals.begin(), intervals.end());
        int res = 0;
        int prev_end = -int(5e4);
        for (auto &it : intervals) {
            int s = it[0], e = it[1];
            if (s >= prev_end)
                prev_end = e;
            else {
                res ++;
                prev_end = min(e, prev_end);
            }
        }
        return res;
    }
};
```

</details>

## meeting rooms ii
Problem Link: https://leetcode.com/problems/meeting-rooms-ii

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## task scheduler
Problem Link: https://leetcode.com/problems/task-scheduler

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def leastInterval(self, tasks: List[str], n: int) -> int:
        cnt = {}
        max_cnt = 0
        for i in tasks:
            cnt[i] = cnt.get(i, 0) + 1
            max_cnt = max(max_cnt, cnt[i])
        res = (max_cnt-1) * (n+1)
        for i, j in cnt.items():
            if j == max_cnt:
                res += 1
        return max(res, len(tasks))
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int leastInterval(vector<char> &tasks, int n) {
        map<char, int> cnt;
        int max_cnt = 0;
        for (char i : tasks) {
            cnt[i] ++;
            max_cnt = max(max_cnt, cnt[i]);
        }
        int res = (max_cnt-1) * (n+1);
        for (auto &[i, j] : cnt) {
            if (j == max_cnt)
                res ++;
        }
        return max(res, int(size(tasks)));
    }
};
```

</details>

## minimum number of arrows to burst balloons
Problem Link: https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def findMinArrowShots(self, points: List[List[int]]) -> int:
        points.sort()
        res = 0
        prev_end = -int(1<<31)-1
        for s, e in points:
            if s > prev_end:
                prev_end = e
            else:
                res += 1
                prev_end = min(e, prev_end)
        return len(points) - res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int findMinArrowShots(vector<vector<int>> &points) {
        sort(points.begin(), points.end());
        int res = 0;
        long prev_end = -long(1LL<<31)-1;
        for (auto &it : points) {
            int s = it[0], e = it[1];
            if (s > prev_end)
                prev_end = e;
            else {
                res ++;
                prev_end = min(long(e), prev_end);
            }
        }
        return size(points) - res;
    }
};
```

</details>

## insert interval
Problem Link: https://leetcode.com/problems/insert-interval

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def insert(self, intervals: List[List[int]], newInterval: List[int]) -> List[List[int]]:
        i = 0
        res = []
        while i < len(intervals) and newInterval[0] > intervals[i][1]:
            res.append(intervals[i])
            i += 1
        while i < len(intervals) and newInterval[1] >= intervals[i][0]:
            newInterval = (min(newInterval[0], intervals[i][0]),
                           max(newInterval[1], intervals[i][1]))
            i += 1
        res.append(newInterval)
        while i < len(intervals):
            res.append(intervals[i])
            i += 1
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<vector<int>> insert(vector<vector<int>> &intervals, vector<int> &newInterval) {
        int i = 0;
        vector<vector<int>> res;
        while (i < size(intervals) and newInterval[0] > intervals[i][1]) {
            res.push_back(intervals[i]);
            i ++;
        }
        while (i < size(intervals) and newInterval[1] >= intervals[i][0]) {
            newInterval = {min(newInterval[0], intervals[i][0]),
                           max(newInterval[1], intervals[i][1])};
            i ++;
        }
        res.push_back(newInterval);
        while (i < size(intervals)) {
            res.push_back(intervals[i]);
            i ++;
        }
        return res;
    }
};
```

</details>

## find minimum in rotated sorted array
Problem Link: https://leetcode.com/problems/find-minimum-in-rotated-sorted-array

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def findMin(self, nums: List[int]) -> int:
        l, r = 0, len(nums)-1
        while l+1 < r:
            m = (l+r) // 2
            if nums[m] > nums[r]:
                l = m
            else:
                r = m
        return min(nums[l], nums[r])
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int findMin(vector<int> &nums) {
        int l = 0, r = size(nums)-1;
        while (l+1 < r) {
            int m = (l+r) / 2;
            if (nums[m] > nums[r])
                l = m;
            else
                r = m;
        }
        return min(nums[l], nums[r]);
    }
};
```

</details>

## find peak element
Problem Link: https://leetcode.com/problems/find-peak-element

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def findPeakElement(self, nums: List[int]) -> int:
        l, r = 0, len(nums)-1
        while l < r:
            m = (l+r) // 2
            if nums[m] > nums[m+1]:
                r = m
            else:
                l = m+1
        return l
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int findPeakElement(vector<int> &nums) {
        int l = 0, r = size(nums)-1;
        while (l < r) {
            int m = (l+r) / 2;
            if (nums[m] > nums[m+1])
                r = m;
            else
                l = m+1;
        }
        return l;
    }
};
```

</details>

## search in rotated sorted array
Problem Link: https://leetcode.com/problems/search-in-rotated-sorted-array

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        l, r = 0, len(nums)-1
        while l <= r:
            m = (l+r) // 2
            if target == nums[m]:
                return m
            if nums[l] <= nums[m]:
                if target > nums[m] or target < nums[l]:
                    l = m+1
                else:
                    r = m-1
            else:
                if target < nums[m] or target > nums[r]:
                    r = m-1
                else:
                    l = m+1
        return -1
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int l = 0, r = size(nums)-1;
        while (l <= r) {
            int m = (l+r) / 2;
            if (target == nums[m])
                return m;
            if (nums[l] <= nums[m]) {
                if (target > nums[m] or target < nums[l])
                    l = m+1;
                else
                    r = m-1;
            }
            else {
                if (target < nums[m] or target > nums[r])
                    r = m-1;
                else
                    l = m+1;
            }
        }
        return -1;
    }
};
```

</details>

## search in rotated sorted array ii
Problem Link: https://leetcode.com/problems/search-in-rotated-sorted-array-ii

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def search(self, nums: List[int], target: int) -> bool:
        l, r = 0, len(nums)-1
        while l <= r:
            m = (l+r) // 2
            if target == nums[m]:
                return True
            if nums[l] < nums[m]:
                if target > nums[m] or target < nums[l]:
                    l = m+1
                else:
                    r = m-1
            elif nums[l] > nums[m]:
                if target < nums[m] or target > nums[r]:
                    r = m-1
                else:
                    l = m+1
            else:
                l += 1
        return False
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    bool search(vector<int> &nums, int target) {
        int l = 0, r = size(nums)-1;
        while (l <= r) {
            int m = (l+r) / 2;
            if (target == nums[m])
                return true;
            if (nums[l] < nums[m]) {
                if (target > nums[m] or target < nums[l])
                    l = m+1;
                else
                    r = m-1;
            }
            else if (nums[l] > nums[m]) {
                if (target < nums[m] or target > nums[r])
                    r = m-1;
                else
                    l = m+1;
            }
            else
                l ++;
        }
        return false;
    }
};
```

</details>

## search a 2d matrix
Problem Link: https://leetcode.com/problems/search-a-2d-matrix

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        n, m = len(matrix), len(matrix[0])
        l, r = 0, n*m-1
        while l <= r:
            k = (l+r) // 2
            i, j = k//m, k%m
            if matrix[i][j] > target:
                r = k-1
            elif matrix[i][j] < target:
                l = k+1
            else:
                return True
        return False
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    bool searchMatrix(vector<vector<int>> &matrix, int target) {
        int n = size(matrix), m = size(matrix[0]);
        int l = 0, r = n*m-1;
        while (l <= r) {
            int k = (l+r) / 2;
            int i = k/m, j = k%m;
            if (matrix[i][j] > target)
                r = k-1;
            else if (matrix[i][j] < target)
                l = k+1;
            else
                return true;
        }
        return false;
    }
};
```

</details>

## search a 2d matrix ii
Problem Link: https://leetcode.com/problems/search-a-2d-matrix-ii

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        n, m = len(matrix), len(matrix[0])
        i, j = 0, m-1
        while i < n and j >= 0:
            if matrix[i][j] > target:
                j -= 1
            elif matrix[i][j] < target:
                i += 1
            else:
                return True;
        return False
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    bool searchMatrix(vector<vector<int>> &matrix, int target) {
        int n = size(matrix), m = size(matrix[0]);
        int i = 0, j = m-1;
        while (i < n and j >= 0) {
            if (matrix[i][j] > target)
                j --;
            else if (matrix[i][j] < target)
                i ++;
            else
                return true;
        }
        return false;
    }
};
```

</details>

## find k closest elements
Problem Link: https://leetcode.com/problems/find-k-closest-elements

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def findClosestElements(self, arr: List[int], k: int, x: int) -> List[int]:
        l, r = 0, len(arr)-k
        while l < r:
            m = (l+r) // 2
            if x - arr[m] > arr[m+k] - x:
                l = m+1
            else:
                r = m
        return arr[l:l+k]
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<int> findClosestElements(vector<int>& arr, int k, int x) {
        int l = 0, r = size(arr)-k;
        while (l < r) {
            int m = (l+r) / 2;
            if (x - arr[m] > arr[m+k] - x)
                l = m+1;
            else
                r = m;
        }
        vector<int> res(arr.begin()+l, arr.begin()+l+k);
        return res;
    }
};
```

</details>

## minimum size subarray sum
Problem Link: https://leetcode.com/problems/minimum-size-subarray-sum

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        i, total, res = 0, 0, 2e9
        for j in range(len(nums)):
            total += nums[j]
            while total >= target:
                res = min(res, j-i+1)
                total -= nums[i]
                i += 1
        return 0 if res == 2e9 else res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int minSubArrayLen(int target, vector<int> &nums) {
        int i = 0, total = 0, res = 2e9;
        for (int j=0; j<size(nums); j++) {
            total += nums[j];
            while (total >= target) {
                res = min(res, j-i+1);
                total -= nums[i];
                i ++;
            }
        }
        return res == 2e9 ? 0 : res;
    }
};
```

</details>

## fruit into baskets
Problem Link: https://leetcode.com/problems/fruit-into-baskets

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def totalFruit(self, fruits: List[int]) -> int:
        cnt = {}
        res, i = 0, 0
        for j in range(len(fruits)):
            cnt[fruits[j]] = cnt.get(fruits[j], 0) + 1
            while len(cnt) > 2:
                cnt[fruits[i]] -= 1
                if cnt[fruits[i]] == 0:
                    cnt.pop(fruits[i])
                i += 1
            res = max(res, j-i+1)
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int totalFruit(vector<int> &fruits) {
        map<int, int> cnt;
        int res = 0, i = 0;
        for (int j=0; j<size(fruits); j++) {
            cnt[fruits[j]] ++;
            while (size(cnt) > 2) {
                cnt[fruits[i]] --;
                if (cnt[fruits[i]] == 0)
                    cnt.erase(fruits[i]);
                i ++;
            }
            res = max(res, j-i+1);
        }
        return res;
    }
};
```
