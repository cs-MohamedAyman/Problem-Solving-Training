<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="80" src="/logos/leetcode.png"></img></a>

# LeetCode OJ - Interviews Questions <br> Medium Problems III `35 problems`

## permutation in string
Problem Link: https://leetcode.com/problems/permutation-in-string

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

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

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

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

</details>

## longest repeating character replacement
Problem Link: https://leetcode.com/problems/longest-repeating-character-replacement

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

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

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

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

</details>

## longest substring without repeating characters
Problem Link: https://leetcode.com/problems/longest-substring-without-repeating-characters

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

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

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

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

</details>

## kth smallest element in a bst
Problem Link: https://leetcode.com/problems/kth-smallest-element-in-a-bst

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

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

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

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

</details>

## k closest points to origin
Problem Link: https://leetcode.com/problems/k-closest-points-to-origin

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

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

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<vector<int>> kClosest(vector<vector<int>> &points, int k) {
        auto comp = [](const pair<int, int> &x, const pair<int, int> &y) { return x.first > y.first; };
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

</details>

## top k frequent elements
Problem Link: https://leetcode.com/problems/top-k-frequent-elements

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

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

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

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

</details>

## sort characters by frequency
Problem Link: https://leetcode.com/problems/sort-characters-by-frequency

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

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

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

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

</details>

## kth largest element in an array
Problem Link: https://leetcode.com/problems/kth-largest-element-in-an-array

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

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

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

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

</details>

## reorganize string
Problem Link: https://leetcode.com/problems/reorganize-string

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

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

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    string reorganizeString(string s) {
        map<char, int> cnt;
        for (char i : s)
            cnt[i] ++;
        auto comp = [](const pair<char,int> &a, const pair<char,int> &b) { return a.second < b.second; };
        auto max_val = max_element(cnt.begin(), cnt.end(), comp);
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

</details>

## course schedule
Problem Link: https://leetcode.com/problems/course-schedule

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

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

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

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

</details>

## course schedule ii
Problem Link: https://leetcode.com/problems/course-schedule-ii

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

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

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

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

</details>

## minimum height trees
Problem Link: https://leetcode.com/problems/minimum-height-trees

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

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
        while q:
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

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

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

</details>

## sequence reconstruction
Problem Link: https://leetcode.com/problems/sequence-reconstruction

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## binary tree level order traversal ii
Problem Link: https://leetcode.com/problems/binary-tree-level-order-traversal-ii

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def levelOrderBottom(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []
        q = [root]
        res = []
        while q:
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

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

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

</details>

## binary tree level order traversal
Problem Link: https://leetcode.com/problems/binary-tree-level-order-traversal

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []
        q = [root]
        res = []
        while q:
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

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

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

</details>

## binary tree zigzag level order traversal
Problem Link: https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def zigzagLevelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []
        q = [root]
        res = []
        is_reverse = 0
        while q:
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

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

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

</details>

## populating next right pointers in each node
Problem Link: https://leetcode.com/problems/populating-next-right-pointers-in-each-node

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def connect(self, root: 'Optional[Node]') -> 'Optional[Node]':
        if not root:
            return root
        q = [root]
        while q:
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

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

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

</details>

## populating next right pointers in each node ii
Problem Link: https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def connect(self, root: 'Node') -> 'Node':
        if not root:
            return root
        q = [root]
        while q:
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

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

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

</details>

## binary tree right side view
Problem Link: https://leetcode.com/problems/binary-tree-right-side-view

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def rightSideView(self, root: Optional[TreeNode]) -> List[int]:
        if not root:
            return []
        q = [root]
        res = []
        while q:
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

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

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

</details>

## all nodes distance k in binary tree
Problem Link: https://leetcode.com/problems/all-nodes-distance-k-in-binary-tree

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def distanceK(self, root: TreeNode, target: TreeNode, k: int) -> List[int]:
        def bfs():
            q = [(-1, root)]
            while q:
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

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

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

</details>

## path sum ii
Problem Link: https://leetcode.com/problems/path-sum-ii

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def pathSum(self, root: Optional[TreeNode], targetSum: int) -> List[List[int]]:
        def dfs(curr_node, curr_sum, curr_path):
            if not curr_node.left and not curr_node.right:
                if curr_sum == 0:
                    res.append(curr_path)
                return
            if curr_node.left:
                dfs(curr_node.left,  curr_sum-curr_node.left.val,
                    curr_path+[curr_node.left.val])
            if curr_node.right:
                dfs(curr_node.right, curr_sum-curr_node.right.val,
                    curr_path+[curr_node.right.val])

        if not root:
            return []
        res = []
        dfs(root, targetSum-root.val, [root.val])
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    void dfs(TreeNode *curr_node, int curr_sum, vector<int> curr_path,
             vector<vector<int>> &res) {
        if (not curr_node->left and not curr_node->right) {
            if (curr_sum == 0)
                res.push_back(curr_path);
            return;
        }
        if (curr_node->left) {
            curr_path.push_back(curr_node->left->val);
            dfs(curr_node->left,  curr_sum-curr_node->left->val,
                curr_path, res);
            curr_path.pop_back();
        }
        if (curr_node->right) {
            curr_path.push_back(curr_node->right->val);
            dfs(curr_node->right, curr_sum-curr_node->right->val,
                curr_path, res);
            curr_path.pop_back();
        }
    }
public:
    vector<vector<int>> pathSum(TreeNode *root, int targetSum) {
        if (not root)
            return {};
        vector<vector<int>> res;
        dfs(root, targetSum-root->val, {root->val}, res);
        return res;
    }
};
```

</details>

## path sum iii
Problem Link: https://leetcode.com/problems/path-sum-iii

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def pathSum(self, root: Optional[TreeNode], targetSum: int) -> int:
        def dfs(curr_node, curr_sum):
            res_left, res_right = 0, 0
            if curr_node.left:
                res_left  = dfs(curr_node.left,  curr_sum-curr_node.left.val)
            if curr_node.right:
                res_right = dfs(curr_node.right, curr_sum-curr_node.right.val)
            return res_left + res_right + int(curr_sum == 0)

        def dfs_tree(curr_node):
            if not curr_node:
                return 0
            return dfs_tree(curr_node.left) + \
                   dfs_tree(curr_node.right) + \
                   dfs(curr_node, targetSum-curr_node.val)

        return dfs_tree(root)
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    int dfs(TreeNode *curr_node, long curr_sum) {
        int res_left = 0, res_right = 0;
        if (curr_node->left)
            res_left  = dfs(curr_node->left,  curr_sum-curr_node->left->val);
        if (curr_node->right)
            res_right = dfs(curr_node->right, curr_sum-curr_node->right->val);
        return res_left + res_right + int(curr_sum == 0);
    }

    int dfs_tree(TreeNode *curr_node, int targetSum) {
        if (not curr_node)
            return 0;
        return dfs_tree(curr_node->left, targetSum) +
               dfs_tree(curr_node->right, targetSum) +
               dfs(curr_node, targetSum-curr_node->val);
    }
public:
    int pathSum(TreeNode *root, int targetSum) {
        return dfs_tree(root, targetSum);
    }
};
```

</details>

## lowest common ancestor of a binary tree
Problem Link: https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        def search(curr, p, q):
            if not curr:
                return curr
            if curr.val == p.val or curr.val == q.val:
                return curr
            left  = search(curr.left,  p, q)
            right = search(curr.right, p, q)
            if left and right:
                return curr
            return left if left else right

        if not root or not p or not q:
            return None
        return search(root, p, q)
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    TreeNode* search(TreeNode *curr, TreeNode *p, TreeNode *q) {
        if (not curr)
            return curr;
        if (curr->val == p->val or curr->val == q->val)
            return curr;
        TreeNode *left  = search(curr->left,  p, q);
        TreeNode *right = search(curr->right, p, q);
        if (left and right)
            return curr;
        return left? left : right;
    }
public:
    TreeNode* lowestCommonAncestor(TreeNode *root, TreeNode *p, TreeNode *q) {
        if (not root or not p or not q)
            return NULL;
        return search(root, p, q);
    }
};
```

</details>

## maximum binary tree
Problem Link: https://leetcode.com/problems/maximum-binary-tree

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def constructMaximumBinaryTree(self, nums: List[int]) -> Optional[TreeNode]:
        def build_tree(nums):
            if len(nums) == 0:
                return None
            i = nums.index(max(nums))
            left_nums  = nums[:i]
            right_nums = nums[i+1:]
            root = TreeNode(max(nums))
            root.left  = build_tree(left_nums)
            root.right = build_tree(right_nums)
            return root

        return build_tree(nums)
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    TreeNode* build_tree(vector<int> nums) {
        if (size(nums) == 0)
            return NULL;
        int i = max_element(nums.begin(), nums.end()) - nums.begin();
        vector<int> left_nums(nums.begin(), nums.begin()+i);
        vector<int> right_nums(nums.begin()+i+1, nums.end());
        TreeNode *root = new TreeNode(*max_element(nums.begin(), nums.end()));
        root->left  = build_tree(left_nums);
        root->right = build_tree(right_nums);
        return root;
    }
public:
    TreeNode* constructMaximumBinaryTree(vector<int> &nums) {
        return build_tree(nums);
    }
};
```

</details>

## maximum width of binary tree
Problem Link: https://leetcode.com/problems/maximum-width-of-binary-tree

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def widthOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        q = [(root, 0)]
        res = 0
        while q:
            curr_len = len(q)
            prt_width = q[0][1]
            last_width = -1
            for i in range(curr_len):
                curr, width = q.pop(0)
                if curr.left:
                    q.append((curr.left,  2*width - 2*prt_width))
                if curr.right:
                    q.append((curr.right, 2*width+1 - 2*prt_width))
                last_width = width
            res = max(res, last_width-prt_width+1)
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int widthOfBinaryTree(TreeNode *root) {
        vector<pair<TreeNode*, long>> q = {{root, 0}};
        int res = 0;
        while (size(q)) {
            int curr_len = size(q);
            int prt_width = q[0].second;
            int last_width;
            for (int i=0; i<curr_len; i++) {
                auto [curr, width] = q[0];
                q.erase(q.begin());
                if (curr->left)
                    q.push_back({curr->left,  2*width - 2*prt_width});
                if (curr->right)
                    q.push_back({curr->right, 2*width+1 - 2*prt_width});
                last_width = width;
            }
            res = max(res, last_width-prt_width+1);
        }
        return res;
    }
};
```

</details>

## construct binary tree from preorder and inorder traversal
Problem Link: https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> Optional[TreeNode]:
        def build_tree(preorder, inorder):
            if len(preorder) == 0 or len(inorder) == 0:
                return None
            i = inorder.index(preorder[0])
            left_inorder  = inorder[:i]
            right_inorder = inorder[i+1:]
            left_preorder  = preorder[1:i+1]
            right_preorder = preorder[i+1:]
            root = TreeNode(preorder[0])
            root.left  = build_tree(left_preorder, left_inorder)
            root.right = build_tree(right_preorder, right_inorder)
            return root

        return build_tree(preorder, inorder)
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    TreeNode* build_tree(vector<int> preorder, vector<int> inorder) {
        if (size(preorder) == 0 or size(inorder) == 0)
            return NULL;
        int i = find(inorder.begin(), inorder.end(), preorder[0]) - inorder.begin();
        vector<int> left_inorder(inorder.begin(), inorder.begin()+i);
        vector<int> right_inorder(inorder.begin()+i+1, inorder.end());
        vector<int> left_preorder(preorder.begin()+1, preorder.begin()+i+1);
        vector<int> right_preorder(preorder.begin()+i+1, preorder.end());
        TreeNode *root = new TreeNode(preorder[0]);
        root->left  = build_tree(left_preorder, left_inorder);
        root->right = build_tree(right_preorder, right_inorder);
        return root;
    }
public:
    TreeNode* buildTree(vector<int> &preorder, vector<int> &inorder) {
        return build_tree(preorder, inorder);
    }
};
```

</details>

## validate binary search tree
Problem Link: https://leetcode.com/problems/validate-binary-search-tree

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def isValidBST(self, root: Optional[TreeNode]) -> bool:
        def check_BST(curr, min_val, max_val):
            if not curr:
                return True
            return min_val <= curr.val <= max_val and \
                   check_BST(curr.left, min_val, curr.val-1) and \
                   check_BST(curr.right, curr.val+1, max_val)

        return check_BST(root, -1<<31, 1<<31)
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    bool check_BST(TreeNode *curr, long min_val, long max_val) {
        if (not curr)
            return true;
        return min_val <= curr->val and curr->val <= max_val and
               check_BST(curr->left, min_val, curr->val-1LL) and
               check_BST(curr->right, curr->val+1LL, max_val);
    }
public:
    bool isValidBST(TreeNode *root) {
        return check_BST(root, -long(1LL<<31), long(1LL<<31));
    }
};
```

</details>

## implement trie prefix tree
Problem Link: https://leetcode.com/problems/implement-trie-prefix-tree

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Trie:
    class TrieNode:
        def __init__(self):
            self.child = [None] * 26
            self.end = False

    def __init__(self):
        self.root = self.TrieNode()

    def insert(self, word: str) -> None:
        curr = self.root
        for c in word:
            i = ord(c) - ord('a')
            if curr.child[i] == None:
                curr.child[i] = self.TrieNode()
            curr = curr.child[i]
        curr.end = True

    def search(self, word: str) -> bool:
        curr = self.root
        for c in word:
            i = ord(c) - ord("a")
            if curr.child[i] == None:
                return False
            curr = curr.child[i]
        return curr.end

    def startsWith(self, prefix: str) -> bool:
        curr = self.root
        for c in prefix:
            i = ord(c) - ord("a")
            if curr.child[i] == None:
                return False
            curr = curr.child[i]
        return True
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Trie {
    class TrieNode {
    public:
        vector<TrieNode*> child;
        bool end;
        TrieNode() {
            this->child.assign(26, NULL);
            this->end = false;
        }
    };
    TrieNode *root;
public:
    Trie() {
        this->root = new TrieNode();
    }
    void insert(string word) {
        TrieNode *curr = this->root;
        for (char c : word) {
            int i = c - 'a';
            if (curr->child[i] == NULL)
                curr->child[i] = new TrieNode();
            curr = curr->child[i];
        }
        curr->end = true;
    }
    bool search(string word) {
        TrieNode *curr = this->root;
        for (char c : word) {
            int i = c - 'a';
            if (curr->child[i] == NULL)
                return false;
            curr = curr->child[i];
        }
        return curr->end;
    }
    bool startsWith(string prefix) {
        TrieNode *curr = this->root;
        for (char c : prefix) {
            int i = c - 'a';
            if (curr->child[i] == NULL)
                return false;
            curr = curr->child[i];
        }
        return true;
    }
};
```

</details>

## 3Sum
Problem Link: https://leetcode.com/problems/3sum

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        res = set()
        nums.sort()
        for i in range(len(nums)):
            if i > 0 and nums[i] == nums[i-1]:
                continue
            l, r = i+1, len(nums)-1
            while l < r:
                s = nums[i] + nums[l] + nums[r]
                if s > 0:
                    r -= 1
                elif s <= 0:
                    if s == 0 and (nums[i], nums[l], nums[r]) not in res:
                        res.add((nums[i], nums[l], nums[r]))
                    l += 1
        ans = list(res)
        return ans
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int> &nums) {
        set<vector<int>> res;
        sort(nums.begin(), nums.end());
        for (int i=0; i<size(nums); i++) {
            if (i > 0 and nums[i] == nums[i-1])
                continue;
            int l = i+1, r = size(nums)-1;
            while (l < r) {
                int s = nums[i] + nums[l] + nums[r];
                if (s > 0)
                    r --;
                else if (s <= 0) {
                    if (s == 0 and res.find({nums[i], nums[l], nums[r]}) == res.end())
                        res.insert({nums[i], nums[l], nums[r]});
                    l ++;
                }
            }
        }
        vector<vector<int>> ans(res.begin(), res.end());
        return ans;
    }
};
```

</details>

## 3sum closest
Problem Link: https://leetcode.com/problems/3sum-closest

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def threeSumClosest(self, nums: List[int], target: int) -> int:
        res = 2e4
        nums.sort()
        for i in range(len(nums)):
            if i > 0 and nums[i] == nums[i-1]:
                continue
            l, r = i+1, len(nums)-1
            while l < r:
                s = nums[i] + nums[l] + nums[r]
                if abs(s-target) < abs(res-target):
                    res = s
                if s > target:
                    r -= 1
                elif s <= target:
                    l += 1
                else:
                    return res
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int threeSumClosest(vector<int> &nums, int target) {
        int res = 2e4;
        sort(nums.begin(), nums.end());
        for (int i=0; i<size(nums); i++) {
            if (i > 0 and nums[i] == nums[i-1])
                continue;
            int l = i+1, r = size(nums)-1;
            while (l < r) {
                int s = nums[i] + nums[l] + nums[r];
                if (abs(s-target) < abs(res-target))
                    res = s;
                if (s > target)
                    r --;
                else if (s <= target)
                    l ++;
                else
                    return res;
            }
        }
        return res;
    }
};
```

</details>

## subarray product less than k
Problem Link: https://leetcode.com/problems/subarray-product-less-than-k

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def numSubarrayProductLessThanK(self, nums: List[int], k: int) -> int:
        p, c, i = 1, 0, 0
        for j in range(len(nums)):
            p *= nums[j]
            while i <= j and p >= k:
                p //= nums[i]
                i += 1
            c += j-i+1
        return c
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int numSubarrayProductLessThanK(vector<int> &nums, int k) {
        int p=1, c=0, i=0;
        for (int j=0; j<size(nums); j++) {
            p *= nums[j];
            while (i <= j and p >= k) {
                p /= nums[i];
                i ++;
            }
            c += j-i+1;
        }
        return c;
    }
};
```

</details>

## sort colors
Problem Link: https://leetcode.com/problems/sort-colors

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        def heapify(arr, n, i):
            j = -1
            while i != j:
                j = i
                left_idx  = 2*i+1
                right_idx = 2*i+2
                if left_idx < n and arr[left_idx] > arr[i]:
                    i = left_idx
                if right_idx < n and arr[right_idx] > arr[i]:
                    i = right_idx
                arr[i], arr[j] = arr[j], arr[i]

        def heap_sort(arr, n):
            for i in range(n//2, -1, -1):
                heapify(arr, n, i)
            for i in range(n-1, -1, -1):
                arr[0], arr[i] = arr[i], arr[0]
                heapify(arr, i, 0)

        heap_sort(nums, len(nums))
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    void heapify(vector<int> &arr, int n, int i) {
        int j = -1;
        while (i != j) {
            j = i;
            int left_idx  = 2*i+1;
            int right_idx = 2*i+2;
            if (left_idx < n and arr[left_idx] > arr[i])
                i = left_idx;
            if (right_idx < n and arr[right_idx] > arr[i])
                i = right_idx;
            swap(arr[i], arr[j]);
        }
    }
    void heap_sort(vector<int> &arr, int n) {
        for (int i = n/2; i >= 0; i--)
            heapify(arr, n, i);
        for (int i = n-1; i >= 0; i--) {
            swap(arr[0], arr[i]);
            heapify(arr, i, 0);
        }
    }
public:
    void sortColors(vector<int> &nums) {
        heap_sort(nums, size(nums));
    }
};
```

</details>

## container with most water
Problem Link: https://leetcode.com/problems/container-with-most-water

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        l, r = 0, len(height)-1
        res = 0
        while l < r:
            res = max(res, min(height[l], height[r]) * (r - l))
            if height[l] < height[r]:
                l += 1
            elif height[r] < height[l]:
                r -= 1
            else:
                l += 1
                r -= 1
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int maxArea(vector<int>& height) {
        int l = 0, r = size(height)-1;
        int res = 0;
        while (l < r) {
            res = max(res, min(height[l], height[r]) * (r - l));
            if (height[l] < height[r])
                l ++;
            else if (height[r] < height[l])
                r --;
            else {
                l ++;
                r --;
            }
        }
        return res;
    }
};
```

</details>

## longest word in dictionary
Problem Link: https://leetcode.com/problems/longest-word-in-dictionary

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Trie:
    class TrieNode:
        def __init__(self):
            self.child = [None] * 26
            self.end = False

    def __init__(self):
        self.root = self.TrieNode()

    def insert(self, word: str) -> None:
        curr = self.root
        for c in word:
            i = ord(c) - ord('a')
            if curr.child[i] == None:
                curr.child[i] = self.TrieNode()
            curr = curr.child[i]
        curr.end = True

    def search(self, word: str) -> bool:
        curr = self.root
        for c in word:
            i = ord(c) - ord("a")
            if curr.child[i] == None:
                return False
            curr = curr.child[i]
        return curr.end

    def startsWith(self, prefix: str) -> bool:
        curr = self.root
        for c in prefix:
            i = ord(c) - ord("a")
            if curr.child[i] == None:
                return False
            curr = curr.child[i]
            if not curr.end:
                return False
        return True

class Solution:
    def longestWord(self, words: List[str]) -> str:
        t = Trie()
        words.sort()
        for w in words:
            t.insert(w)
        res = ''
        for w in words:
            if len(w) < len(res) or len(w) == len(res) and w >= res:
                continue
            if t.startsWith(w):
                res = w
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Trie {
    class TrieNode {
    public:
        vector<TrieNode*> child;
        bool end;
        TrieNode() {
            this->child.assign(26, NULL);
            this->end = false;
        }
    };
    TrieNode *root;
public:
    Trie() {
        this->root = new TrieNode();
    }
    void insert(string word) {
        TrieNode *curr = this->root;
        for (char c : word) {
            int i = c - 'a';
            if (curr->child[i] == NULL)
                curr->child[i] = new TrieNode();
            curr = curr->child[i];
        }
        curr->end = true;
    }
    bool search(string word) {
        TrieNode *curr = this->root;
        for (char c : word) {
            int i = c - 'a';
            if (curr->child[i] == NULL)
                return false;
            curr = curr->child[i];
        }
        return curr->end;
    }
    bool startsWith(string prefix) {
        TrieNode *curr = this->root;
        for (char c : prefix) {
            int i = c - 'a';
            if (curr->child[i] == NULL)
                return false;
            curr = curr->child[i];
            if (not curr->end)
                return false;
        }
        return true;
    }
};

class Solution {
public:
    string longestWord(vector<string>& words) {
        Trie t = Trie();
        sort(words.begin(), words.end());
        for (string w : words)
            t.insert(w);
        string res = "";
        for (string w : words) {
            if (size(w) < size(res) or size(w) == size(res) and w >= res)
                continue;
            if (t.startsWith(w))
                res = w;
        }
        return res;
    }
};
```

</details>

## maximum xor of two numbers in an array
Problem Link: https://leetcode.com/problems/maximum-xor-of-two-numbers-in-an-array

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def findMaximumXOR(self, nums: List[int]) -> int:
        mask, res = 0, 0
        for i in range(31, -1, -1):
            mask |= (1 << i)
            prefixes = set()
            for n in nums:
                prefixes.add(mask & n)
            tmp = res | (1 << i)
            for p in prefixes:
                if (tmp ^ p) in prefixes:
                    res = tmp
                    break
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int findMaximumXOR(vector<int> &nums) {
        int mask = 0, res = 0;
        for (int i = 31; i >= 0; i--) {
            mask |= (1 << i);
            set<int> prefixes;
            for (int n : nums)
                prefixes.insert(mask & n);
            int tmp = res | (1 << i);
            for (int p : prefixes) {
                if (prefixes.find((tmp ^ p)) != prefixes.end()) {
                    res = tmp;
                    break;
                }
            }
        }
        return res;
    }
};
```

</details>
