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
