<img align="right" width="80" src="https://github.com/cs-MohamedAyman/Problem-Solving-Training/blob/master/online-judges-logos/leetcode.jpg">

## LeetCode OJ - Phase 4 Interviews Questions - Medium Problems III

### permutation in string:
Problem Link: https://leetcode.com/problems/permutation-in-string

#### - Python Solution
```python
class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:
        if len(s1) > len(s2):
            return False
        cnt1, cnt2 = [0] * 26, [0] * 26
        for i in range(len(s1)):
            cnt1[ord(s1[i]) - ord('a')] += 1
            cnt2[ord(s2[i]) - ord('a')] += 1
        cnt_same = 0
        for i in range(26):
            if cnt1[i] == cnt2[i]:
                cnt_same += 1
        for i in range(len(s1), len(s2)):
            if cnt_same == 26:
                return True
            idx = ord(s2[i]) - ord('a')
            cnt2[idx] += 1
            if cnt1[idx] == cnt2[idx]:
                cnt_same += 1
            elif cnt1[idx] + 1 == cnt2[idx]:
                cnt_same -= 1
            idx = ord(s2[i-len(s1)]) - ord('a')
            cnt2[idx] -= 1
            if cnt1[idx] == cnt2[idx]:
                cnt_same += 1
            elif cnt1[idx] - 1 == cnt2[idx]:
                cnt_same -= 1
        return cnt_same == 26
```
#### - CPP Solution
```cpp
class Solution {
public:
    bool checkInclusion(string s1, string s2) {
        if (size(s1) > size(s2))
            return false;
        vector<int> cnt1(26, 0), cnt2(26, 0);
        for (int i=0; i<size(s1); i++) {
            cnt1[s1[i]-'a'] ++;
            cnt2[s2[i]-'a'] ++;
        }
        int cnt_same = 0;
        for (int i=0; i<26; i++) {
            if (cnt1[i] == cnt2[i])
                cnt_same ++;
        }
        for (int i=size(s1); i<size(s2); i++) {
            if (cnt_same == 26)
                return true;
            int idx = s2[i] - 'a';
            cnt2[idx] ++;
            if (cnt1[idx] == cnt2[idx])
                cnt_same ++;
            else if (cnt1[idx] + 1 == cnt2[idx])
                cnt_same --;
            idx = s2[i-size(s1)] - 'a';
            cnt2[idx] --;
            if (cnt1[idx] == cnt2[idx])
                cnt_same ++;
            else if (cnt1[idx] - 1 == cnt2[idx])
                cnt_same --;
        }
        return cnt_same == 26;
    }
};
```

### longest repeating character replacement:
Problem Link: https://leetcode.com/problems/longest-repeating-character-replacement

#### - Python Solution
```python
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        cnt = {}
        res, j, curr_max = 0, 0, 0
        for i in range(len(s)):
            cnt[s[i]] = cnt.get(s[i], 0) + 1
            curr_max = max(curr_max, cnt[s[i]])
            if i-j+1 - curr_max > k:
                cnt[s[j]] -= 1
                j += 1
            res = max(res, i-j+1)
        return res
```
#### - CPP Solution
```cpp
class Solution {
public:
    int characterReplacement(string s, int k) {
        map<char, int> cnt;
        int res = 0, j = 0, curr_max = 0;
        for (int i=0; i<size(s); i++) {
            cnt[s[i]] ++;
            curr_max = max(curr_max, cnt[s[i]]);
            if (i-j+1 - curr_max > k) {
                cnt[s[j]] --;
                j ++;
            }
            res = max(res, i-j+1);
        }
        return res;
    }
};
```

### longest substring without repeating characters:
Problem Link: https://leetcode.com/problems/longest-substring-without-repeating-characters

#### - Python Solution
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        curr_chars = set()
        res, j = 0, 0
        for i in s:
            while i in curr_chars:
                curr_chars.remove(s[j])
                j += 1
            curr_chars.add(i)
            res = max(res, len(curr_chars))
        return res
```
#### - CPP Solution
```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        set<char> curr_chars;
        int res = 0, j = 0;
        for (char i : s) {
            while (curr_chars.find(i) != curr_chars.end()) {
                curr_chars.erase(curr_chars.find(s[j]));
                j ++;
            }
            curr_chars.insert(i);
            res = max(res, int(size(curr_chars)));
        }
        return res;
    }
};
```

### kth smallest element in a bst:
Problem Link: https://leetcode.com/problems/kth-smallest-element-in-a-bst

#### - Python Solution
```python
class Solution:
    def kthSmallest(self, root: Optional[TreeNode], k: int) -> int:
        stk = []
        curr = root
        while stk or curr:
            while curr:
                stk.append(curr)
                curr = curr.left
            k -= 1
            curr = stk.pop()
            if k == 0:
                return curr.val
            curr = curr.right
        return -1
```
#### - CPP Solution
```cpp
class Solution {
public:
    int kthSmallest(TreeNode *root, int k) {
        stack<TreeNode*> stk;
        TreeNode *curr = root;
        while (size(stk) or curr) {
            while (curr) {
                stk.push(curr);
                curr = curr->left;
            }
            k --;
            curr = stk.top();
            stk.pop();
            if (k == 0)
                return curr->val;
            curr = curr->right;
        }
        return -1;
    }
};
```

### k closest points to origin:
Problem Link: https://leetcode.com/problems/k-closest-points-to-origin

#### - Python Solution
```python
import queue

class Solution:
    def kClosest(self, points: List[List[int]], k: int) -> List[List[int]]:
        min_heap = queue.PriorityQueue()
        for i in range(len(points)):
            dist = points[i][0] ** 2 + points[i][1] ** 2
            min_heap.put((dist, i))
        res = [0] * k
        for i in range(k):
            dist, j = min_heap.get()
            res[i] = points[j]
        return res
```
#### - CPP Solution
```cpp
class Solution {
public:
    vector<vector<int>> kClosest(vector<vector<int>> &points, int k) {
        auto comp = [](const pair<int, int> &x, const pair<int, int> &y) {
            return x.first > y.first;
        };
        priority_queue<pair<int, int>, vector<pair<int, int>>, decltype(comp)> min_heap(comp);
        for (int i=0; i<size(points); i++) {
            int dist = points[i][0] * points[i][0] + points[i][1] * points[i][1];
            min_heap.push({dist, i});
        }
        vector<vector<int>> res(k);
        for (int i=0; i<k; i++) {
            auto [dist, j] = min_heap.top();
            min_heap.pop();
            res[i] = points[j];
        }
        return res;
    }
};
```

### top k frequent elements:
Problem Link: https://leetcode.com/problems/top-k-frequent-elements

#### - Python Solution
```python
import queue

class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        cnt = {}
        for i in nums:
            cnt[i] = cnt.get(i, 0) + 1
        max_heap = queue.PriorityQueue()
        for i, j in cnt.items():
            max_heap.put((-j, i))
        res = [0] * k
        for i in range(k):
            v, j = max_heap.get()
            res[i] = j
        return res
```
#### - CPP Solution
```cpp
class Solution {
public:
    vector<int> topKFrequent(vector<int> &nums, int k) {
        map<int, int> cnt;
        for (int i : nums)
            cnt[i] ++;
        priority_queue<pair<int, int>> max_heap;
        for (auto &[i, j] : cnt)
            max_heap.push({j, i});
        vector<int> res(k);
        for (int i=0; i<k; i++) {
            auto [v, j] = max_heap.top();
            max_heap.pop();
            res[i] = j;
        }
        return res;
    }
};
```

### sort characters by frequency:
Problem Link: https://leetcode.com/problems/sort-characters-by-frequency

#### - Python Solution
```python
import queue

class Solution:
    def frequencySort(self, s: str) -> str:
        cnt = {}
        for i in s:
            cnt[i] = cnt.get(i, 0) + 1
        max_heap = queue.PriorityQueue()
        for i, j in cnt.items():
            max_heap.put((-j, i))
        res = ''
        while not max_heap.empty():
            v, j = max_heap.get()
            res += j * -v
        return res
```
#### - CPP Solution
```cpp
class Solution {
public:
    string frequencySort(string s) {
        map<char, int> cnt;
        for (char i : s)
            cnt[i] ++;
        priority_queue<pair<int, char>> max_heap;
        for (auto &[i, j] : cnt)
            max_heap.push({j, i});
        string res = "";
        while (not max_heap.empty()) {
            auto [v, j] = max_heap.top();
            max_heap.pop();
            res += string(v, j);
        }
        return res;
    }
};
```

### kth largest element in an array:
Problem Link: https://leetcode.com/problems/kth-largest-element-in-an-array

#### - Python Solution
```python
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        def partition(nums, l, r):
            p, f = nums[r], l
            for i in range(l, r):
                if nums[i] <= p:
                    nums[f], nums[i] = nums[i], nums[f]
                    f += 1
            nums[f], nums[r] = nums[r], nums[f]
            return f

        k = len(nums) - k
        l, r = 0, len(nums) - 1
        while l < r:
            p = partition(nums, l, r)
            if p < k:
                l = p+1
            elif p > k:
                r = p-1
            else:
                break
        return nums[k]
```
#### - CPP Solution
```cpp
class Solution {
    int partition(const vector<int> &nums, int l, int r) {
        int p = nums[r], f = l;
        for (int i=l; i<r; i++) {
            if (nums[i] <= p) {
                swap(nums[f], nums[i]);
                f ++;
            }
        }
        swap(nums[f], nums[r]);
        return f;
    }
public:
    int findKthLargest(vector<int> &nums, int k) {
        k = size(nums) - k;
        int l = 0, r = size(nums)-1;
        while (l < r) {
            int p = partition(nums, l, r);
            if (p < k)
                l = p+1;
            else if (p > k)
                r = p-1;
            else
                break;
        }
        return nums[k];
    }
};
```

### reorganize string:
Problem Link: https://leetcode.com/problems/reorganize-string

#### - Python Solution
```python
import queue

class Solution:
    def reorganizeString(self, s: str) -> str:
        cnt = {}
        for i in s:
            cnt[i] = cnt.get(i, 0) + 1
        if max(cnt.values()) > (len(s)+1) // 2:
            return ''
        max_heap = queue.PriorityQueue()
        for i, j in cnt.items():
            max_heap.put((-j, i))
        res, prev = '', None
        while not max_heap.empty():
            v, j = max_heap.get()
            res += j
            if prev:
                max_heap.put(prev)
                prev = None
            if v+1 != 0:
                prev = (v+1, j)
        return res

```
#### - CPP Solution
```cpp
class Solution {
public:
    string reorganizeString(string s) {
        map<char, int> cnt;
        for (char i : s)
            cnt[i] ++;
        auto max_val = max_element(cnt.begin(), cnt.end(),
                                  [] (const pair<char,int> &a, const pair<char,int> &b) {
                                      return a.second < b.second;
                                  });
        if (max_val->second > (size(s)+1) / 2)
            return "";
        priority_queue<pair<int, char>> max_heap;
        for (auto &[i, j] : cnt)
            max_heap.push({j, i});
        string res = "";
        pair<int, char> prev = {-1, '$'};
        while (not max_heap.empty()) {
            auto [v, j] = max_heap.top();
            max_heap.pop();
            res += j;
            if (prev.first != -1) {
                max_heap.push(prev);
                prev = {-1, '$'};
            }
            if (v-1 != 0)
                prev = {v-1, j};
        }
        return res;
    }
};
```

### course schedule:
Problem Link: https://leetcode.com/problems/course-schedule

#### - Python Solution
```python
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        def dfs(u):
            if u in visited:
                return False
            if len(adj[u]) == 0:
                return True
            visited.add(u)
            for v in adj[u]:
                if not dfs(v):
                    return False
            visited.remove(u)
            adj[u] = []
            return True

        adj = {i: [] for i in range(numCourses)}
        for i, j in prerequisites:
            adj[i].append(j)
        visited = set()
        for i in range(numCourses):
            if not dfs(i):
                return False
        return True
```
#### - CPP Solution
```cpp
class Solution {
    bool dfs(int u, set<int> &visited, vector<vector<int>> &adj) {
        if (visited.find(u) != visited.end())
            return false;
        if (size(adj[u]) == 0)
            return true;
        visited.insert(u);
        for (auto v : adj[u]) {
            if (not dfs(v, visited, adj))
                return false;
        }
        visited.erase(visited.find(u));
        adj[u].clear();
        return true;
    }
public:
    bool canFinish(int numCourses, vector<vector<int>> &prerequisites) {
        vector<vector<int>> adj(numCourses);
        for (auto v : prerequisites)
            adj[v[0]].push_back(v[1]);
        set<int> visited;
        for (int i=0; i<numCourses; i++) {
            if (not dfs(i, visited, adj))
                return false;
        }
        return true;
    }
};
```

### course schedule ii:
Problem Link: https://leetcode.com/problems/course-schedule-ii

#### - Python Solution
```python
class Solution:
    def findOrder(self, numCourses: int, prerequisites: List[List[int]]) -> List[int]:
        def dfs(u):
            if u in cycle:
                return False
            if u in visited:
                return True
            cycle.add(u)
            for v in adj[u]:
                if not dfs(v):
                    return False
            cycle.remove(u)
            visited.add(u)
            res.append(u)
            return True

        adj = {i: [] for i in range(numCourses)}
        for i, j in prerequisites:
            adj[i].append(j)
        res = []
        visited, cycle = set(), set()
        for i in range(numCourses):
            if not dfs(i):
                return []
        return res
```
#### - CPP Solution
```cpp
class Solution {
    bool dfs(int u, set<int> &visited, set<int> &cycle,
             vector<vector<int>> &adj, vector<int> &res) {
        if (cycle.find(u) != cycle.end())
            return false;
        if (visited.find(u) != visited.end())
            return true;
        cycle.insert(u);
        for (auto v : adj[u]) {
            if (not dfs(v, visited, cycle, adj, res))
                return false;
        }
        cycle.erase(cycle.find(u));
        visited.insert(u);
        res.push_back(u);
        return true;
    }
public:
    vector<int> findOrder(int numCourses, vector<vector<int>> &prerequisites) {
        vector<vector<int>> adj(numCourses);
        for (auto v : prerequisites)
            adj[v[0]].push_back(v[1]);
        vector<int> res;
        set<int> visited, cycle;
        for (int i=0; i<numCourses; i++) {
            if (not dfs(i, visited, cycle, adj, res))
                return {};
        }
        return res;
    }
};
```

### minimum height trees:
Problem Link: https://leetcode.com/problems/minimum-height-trees

#### - Python Solution
```python
class Solution:
    def findMinHeightTrees(self, n: int, edges: List[List[int]]) -> List[int]:
        if n == 1:
            return [0]
        degree = [0] * n
        adj = {i: [] for i in range(n)}
        for i, j in edges:
            adj[i].append(j)
            adj[j].append(i)
            degree[i] += 1
            degree[j] += 1
        q = []
        for i in range(len(degree)):
            if degree[i] == 1:
                q.append(i)
        res = []
        while len(q):
            res.clear()
            queue_len = len(q)
            for i in range(queue_len):
                u = q.pop(0)
                res.append(u)
                for v in adj[u]:
                    degree[v] -= 1
                    if degree[v] == 1:
                        q.append(v)
        return res
```
#### - CPP Solution
```cpp
class Solution {
public:
    vector<int> findMinHeightTrees(int n, vector<vector<int>> &edges) {
        if (n == 1)
            return {0};
        vector<int> degree(n, 0);
        vector<vector<int>> adj(n);
        for (auto v : edges) {
            adj[v[0]].push_back(v[1]);
            adj[v[1]].push_back(v[0]);
            degree[v[0]] ++;
            degree[v[1]] ++;
        }
        vector<int> q;
        for (int i=0; i<size(degree); i++) {
            if (degree[i] == 1)
                q.push_back(i);
        }
        vector<int> res;
        while (size(q)) {
            res.clear();
            int queue_len = size(q);
            for (int i=0; i<queue_len; i++) {
                int u = q[0];
                q.erase(q.begin());
                res.push_back(u);
                for (int v : adj[u]) {
                    degree[v] --;
                    if (degree[v] == 1)
                        q.push_back(v);
                }
            }
        }
        return res;
    }
};
```

### sequence reconstruction:
Problem Link: https://leetcode.com/problems/sequence-reconstruction

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### binary tree level order traversal ii:
Problem Link: https://leetcode.com/problems/binary-tree-level-order-traversal-ii

#### - Python Solution
```python
class Solution:
    def levelOrderBottom(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []
        q = [root]
        res = []
        while len(q):
            level = []
            curr_len = len(q)
            for i in range(curr_len):
                curr = q.pop(0)
                level.append(curr.val)
                if curr.left:
                    q.append(curr.left)
                if curr.right:
                    q.append(curr.right)
            res.append(level)
        res = res[::-1]
        return res
```
#### - CPP Solution
```cpp
class Solution {
public:
    vector<vector<int>> levelOrderBottom(TreeNode *root) {
        if (not root)
            return {};
        vector<TreeNode*> q = {root};
        vector<vector<int>> res;
        while (size(q)) {
            vector<int> level;
            int curr_len = size(q);
            for (int i=0; i<curr_len; i++) {
                TreeNode *curr = q[0];
                q.erase(q.begin());
                level.push_back(curr->val);
                if (curr->left)
                    q.push_back(curr->left);
                if (curr->right)
                    q.push_back(curr->right);
            }
            res.push_back(level);
        }
        reverse(res.begin(), res.end());
        return res;
    }
};
```

### binary tree level order traversal:
Problem Link: https://leetcode.com/problems/binary-tree-level-order-traversal

#### - Python Solution
```python
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []
        q = [root]
        res = []
        while len(q):
            level = []
            curr_len = len(q)
            for i in range(curr_len):
                curr = q.pop(0)
                level.append(curr.val)
                if curr.left:
                    q.append(curr.left)
                if curr.right:
                    q.append(curr.right)
            res.append(level)
        return res
```
#### - CPP Solution
```cpp
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode *root) {
        if (not root)
            return {};
        vector<TreeNode*> q = {root};
        vector<vector<int>> res;
        while (size(q)) {
            vector<int> level;
            int curr_len = size(q);
            for (int i=0; i<curr_len; i++) {
                TreeNode *curr = q[0];
                q.erase(q.begin());
                level.push_back(curr->val);
                if (curr->left)
                    q.push_back(curr->left);
                if (curr->right)
                    q.push_back(curr->right);
            }
            res.push_back(level);
        }
        return res;
    }
};
```

### binary tree zigzag level order traversal:
Problem Link: https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal

#### - Python Solution
```python
class Solution:
    def zigzagLevelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []
        q = [root]
        res = []
        is_reverse = 0
        while len(q):
            level = []
            curr_len = len(q)
            for i in range(curr_len):
                curr = q.pop(0)
                level.append(curr.val)
                if curr.left:
                    q.append(curr.left)
                if curr.right:
                    q.append(curr.right)
            if is_reverse:
                level = level[::-1]
            is_reverse = 1 - is_reverse
            res.append(level)
        return res
```
#### - CPP Solution
```cpp
class Solution {
public:
    vector<vector<int>> zigzagLevelOrder(TreeNode *root) {
        if (not root)
            return {};
        vector<TreeNode*> q = {root};
        vector<vector<int>> res;
        bool is_reverse = 0;
        while (size(q)) {
            vector<int> level;
            int curr_len = size(q);
            for (int i=0; i<curr_len; i++) {
                TreeNode *curr = q[0];
                q.erase(q.begin());
                level.push_back(curr->val);
                if (curr->left)
                    q.push_back(curr->left);
                if (curr->right)
                    q.push_back(curr->right);
            }
            if (is_reverse)
                reverse(level.begin(), level.end());
            is_reverse = 1 - is_reverse;
            res.push_back(level);
        }
        return res;
    }
};

```

### populating next right pointers in each node:
Problem Link: https://leetcode.com/problems/populating-next-right-pointers-in-each-node

#### - Python Solution
```python
class Solution:
    def connect(self, root: 'Optional[Node]') -> 'Optional[Node]':
        if not root:
            return root
        q = [root]
        while len(q):
            level = []
            curr_len = len(q)
            prev = None
            for i in range(curr_len):
                curr = q.pop(0)
                if curr.left and curr.right:
                    curr.left.next = curr.right
                    q.append(curr.left)
                    q.append(curr.right)
                    if prev != None:
                        prev.right.next = curr.left
                prev = curr
        return root
```
#### - CPP Solution
```cpp
class Solution {
public:
    Node* connect(Node *root) {
        if (not root)
            return root;
        vector<Node*> q = {root};
        while (size(q)) {
            vector<int> level;
            int curr_len = size(q);
            Node *prev = NULL;
            for (int i=0; i<curr_len; i++) {
                Node *curr = q[0];
                q.erase(q.begin());
                level.push_back(curr->val);
                if (curr->left and curr->right) {
                    curr->left->next = curr->right;
                    q.push_back(curr->left);
                    q.push_back(curr->right);
                    if (prev != NULL)
                        prev->right->next = curr->left;
                }
                prev = curr;
            }
        }
        return root;
    }
};
```

### populating next right pointers in each node ii:
Problem Link: https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii

#### - Python Solution
```python
class Solution:
    def connect(self, root: 'Node') -> 'Node':
        if not root:
            return root
        q = [root]
        while len(q):
            level = []
            curr_len = len(q)
            for i in range(curr_len):
                curr = q.pop(0)
                level.append(curr)
                if curr.left:
                    q.append(curr.left)
                if curr.right:
                    q.append(curr.right)
            for i in range(len(level)-1):
                level[i].next = level[i+1]
        return root
```
#### - CPP Solution
```cpp
class Solution {
public:
    Node* connect(Node *root) {
        if (not root)
            return root;
        vector<Node*> q = {root};
        while (size(q)) {
            vector<Node*> level;
            int curr_len = size(q);
            for (int i=0; i<curr_len; i++) {
                Node *curr = q[0];
                q.erase(q.begin());
                level.push_back(curr);
                if (curr->left)
                    q.push_back(curr->left);
                if (curr->right)
                    q.push_back(curr->right);
            }
            for (int i=0; i<size(level)-1; i++)
                level[i]->next = level[i+1];
        }
        return root;
    }
};
```

### binary tree right side view:
Problem Link: https://leetcode.com/problems/binary-tree-right-side-view

#### - Python Solution
```python
class Solution:
    def rightSideView(self, root: Optional[TreeNode]) -> List[int]:
        if not root:
            return []
        q = [root]
        res = []
        while len(q):
            level = []
            curr_len = len(q)
            for i in range(curr_len):
                curr = q.pop(0)
                level.append(curr.val)
                if curr.left:
                    q.append(curr.left)
                if curr.right:
                    q.append(curr.right)
            res.append(level[-1])
        return res
```
#### - CPP Solution
```cpp
class Solution {
public:
    vector<int> rightSideView(TreeNode* root) {
        if (not root)
            return {};
        vector<TreeNode*> q = {root};
        vector<int> res;
        while (size(q)) {
            vector<int> level;
            int curr_len = size(q);
            for (int i=0; i<curr_len; i++) {
                TreeNode *curr = q[0];
                q.erase(q.begin());
                level.push_back(curr->val);
                if (curr->left)
                    q.push_back(curr->left);
                if (curr->right)
                    q.push_back(curr->right);
            }
            res.push_back(level[size(level)-1]);
        }
        return res;
    }
};
```

### all nodes distance k in binary tree:
Problem Link: https://leetcode.com/problems/all-nodes-distance-k-in-binary-tree

#### - Python Solution
```python
class Solution:
    def distanceK(self, root: TreeNode, target: TreeNode, k: int) -> List[int]:
        def bfs():
            q = [(-1, root)]
            while len(q):
                curr_len = len(q)
                for i in range(curr_len):
                    p, u = q.pop(0)
                    if p != -1:
                        adj[u.val].append(p.val)
                        adj[p.val].append(u.val)
                    if u.left:
                        q.append((u, u.left))
                    if u.right:
                        q.append((u, u.right))

        def dfs(p, u, k):
            if k == 0:
                res.add(u)
                return
            for v in adj[u]:
                if v != p and v not in res:
                    dfs(u, v, k-1)

        adj = {i:[] for i in range(501)}
        bfs()
        res = set()
        dfs(-1, target.val, k)
        res = list(res)
        return res
```
#### - CPP Solution
```cpp
class Solution {
    void bfs(vector<vector<int>> &adj, TreeNode* root) {
        vector<pair<TreeNode*, TreeNode*>> q = {{NULL, root}};
        while (size(q)) {
            int curr_len = size(q);
            for (int i=0; i<curr_len; i++) {
                auto [p, u] = q[0];
                q.erase(q.begin());
                if (p != NULL) {
                    adj[u->val].push_back(p->val);
                    adj[p->val].push_back(u->val);
                }
                if (u->left)
                    q.push_back({u, u->left});
                if (u->right)
                    q.push_back({u, u->right});
            }
        }
    }
    void dfs(int p, int u, int k, set<int> &res, const vector<vector<int>> &adj) {
        if (k == 0) {
            res.insert(u);
            return;
        }
        for (int v : adj[u]) {
            if (v != p and res.find(v) == res.end())
                dfs(u, v, k-1, res, adj);
        }
    }
public:
    vector<int> distanceK(TreeNode *root, TreeNode *target, int k) {
        vector<vector<int>> adj(501);
        bfs(adj, root);
        set<int> res;
        dfs(-1, target->val, k, res, adj);
        vector<int> ans(res.begin(), res.end());
        return ans;
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
