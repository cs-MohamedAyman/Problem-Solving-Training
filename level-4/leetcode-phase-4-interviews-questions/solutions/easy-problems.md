<img align="right" width="80" src="https://github.com/cs-MohamedAyman/Problem-Solving-Training/blob/master/online-judges-logos/leetcode.jpg">

## LeetCode OJ - Phase 4 Interviews Questions - Easy Problems

### contains duplicate: 
https://leetcode.com/problems/contains-duplicate

#### - Python Solution
```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        return len(nums) != len(set(nums))
```
#### - CPP Solution
```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        set<int> set_nums(nums.begin(), nums.end());
        return nums.size() != set_nums.size();
    }
};
```

### missing number: 
https://leetcode.com/problems/missing-number

#### - Python Solution
```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        n = len(nums)
        return n*(n+1)//2 - sum(nums)
```
#### - CPP Solution
```cpp
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int n = nums.size();
        return n*(n+1)/2 - accumulate(nums.begin(), nums.end(), 0);
    }
};
```

### find all numbers disappeared in an array: 
https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array

#### - Python Solution
```python
class Solution:
    def findDisappearedNumbers(self, nums: List[int]) -> List[int]:
        set_nums = set(nums)
        disappeared_num  = []
        for i in range(1, len(nums)+1):
            if i not in set_nums:
                disappeared_num.append(i)
        return disappeared_num
```
#### - CPP Solution
```cpp
class Solution {
public:
    vector<int> findDisappearedNumbers(vector<int>& nums) {
        set<int> set_nums(nums.begin(), nums.end());
        vector<int> disappeared_num;
        for (int i=1; i<nums.size()+1; i++) {
            if (set_nums.find(i) == set_nums.end())
                disappeared_num.push_back(i);
        }
        return disappeared_num;
    }
};
```

### single number: 
https://leetcode.com/problems/single-number

#### - Python Solution
```python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        cnt_nums = [0] * int(6e4)
        for i in nums:
            cnt_nums[i+int(3e4)] += 1
        for i in nums:
            if cnt_nums[i+int(3e4)] == 1:
                return i
        return 0
```
#### - CPP Solution
```cpp
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        vector<int> cnt_nums(6e4, 0);
        for (int i:nums)
            cnt_nums[i+int(3e4)] ++;
        for (int i:nums) {
            if (cnt_nums[i+int(3e4)] == 1)
                return i;
        }
        return 0;
    }
};
```

### climbing stairs: 
https://leetcode.com/problems/climbing-stairs

#### - Python Solution
```python
class Solution:
    def climbStairs(self, n: int) -> int:
        memo = [0] * 46
        memo[0] = memo[1] = 1
        for i in range(2, n+1):
            memo[i] = memo[i-1] + memo[i-2]
        return memo[n]
```
#### - CPP Solution
```cpp
class Solution {
public:
    int climbStairs(int n) {
        vector<int> memo(46, 0);
        memo[0] = memo[1] = 1;
        for (int i=2; i<n+1; i++)
            memo[i] = memo[i-1] + memo[i-2];
        return memo[n];
    }
};
```

### best time to buy and sell stock: 
https://leetcode.com/problems/best-time-to-buy-and-sell-stock

#### - Python Solution
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        min_vals = [1e4] * int(1e5+1)
        max_vals = [0]   * int(1e5+1)
        for i in range(len(prices)):
            min_vals[i+1] = min(min_vals[i], prices[i])
        for i in range(len(prices)-1, -1, -1):
            max_vals[i+1] = max(max_vals[i], prices[i])
        max_profit = 0
        for i in range(1, len(prices)+1):
            max_profit = max(max_profit, max_vals[i]-min_vals[i])
        return max_profit
```
#### - CPP Solution
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        vector<int> min_vals(1e5+1, 1e4);
        vector<int> max_vals(1e5+1, 0);
        for (int i=0; i<prices.size(); i++)
            min_vals[i+1] = min(min_vals[i], prices[i]);
        for (int i=prices.size()-1; i>-1; i--)
            max_vals[i+1] = max(max_vals[i], prices[i]);
        int max_profit = 0;
        for (int i=1; i<prices.size()+1; i++)
            max_profit = max(max_profit, max_vals[i]-min_vals[i]);
        return max_profit;
    }
};
```

### maximum subarray: 
https://leetcode.com/problems/maximum-subarray

#### - Python Solution
```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        curr_subarray_sum = 0
        max_subarray_sum = nums[0]
        for i in nums:
            curr_subarray_sum = max(curr_subarray_sum, 0)
            curr_subarray_sum += i
            max_subarray_sum = max(max_subarray_sum, curr_subarray_sum)
        return max_subarray_sum
```
#### - CPP Solution
```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int curr_subarray_sum = 0;
        int max_subarray_sum = nums[0];
        for (int i : nums) {
            curr_subarray_sum = max(curr_subarray_sum, 0);
            curr_subarray_sum += i;
            max_subarray_sum = max(max_subarray_sum, curr_subarray_sum);
        }
        return max_subarray_sum;
    }
};
```

### range sum query immutable: 
https://leetcode.com/problems/range-sum-query-immutable

#### - Python Solution
```python
class NumArray:
    def __init__(self, nums: List[int]):
        self.cumulative_sum = nums.copy()
        self.cumulative_sum.insert(0, 0)
        for i in range(1, len(nums)+1):
            self.cumulative_sum[i] += self.cumulative_sum[i-1]

    def sumRange(self, left: int, right: int) -> int:
        return self.cumulative_sum[right+1] - self.cumulative_sum[left]
```
#### - CPP Solution
```cpp
class NumArray {
public:
    vector<int> cumulative_sum;
    NumArray(vector<int>& nums) {
        cumulative_sum.assign(nums.begin(), nums.end());
        cumulative_sum.insert(cumulative_sum.begin(), 0);
        for (int i=1; i<nums.size()+1; i++)
            cumulative_sum[i] += cumulative_sum[i-1];
    }
    
    int sumRange(int left, int right) {
        return cumulative_sum[right+1] - cumulative_sum[left];
    }
};
```

### counting bits: 
https://leetcode.com/problems/counting-bits

#### - Python Solution
```python
class Solution:
    def countBits(self, n: int) -> List[int]:
        cnt_ones = [0] * (n+1)
        for i in range(n+1):
            x = i
            cnt = 0
            while x > 0:
                cnt += x%2
                x //= 2
            cnt_ones[i] = cnt
        return cnt_ones
```
#### - CPP Solution
```cpp
class Solution {
public:
    vector<int> countBits(int n) {
        vector<int> cnt_ones (n+1, 0);
        for (int i=0; i<n+1; i++) {
            int x = i;
            int cnt = 0;
            while (x > 0) {
                cnt += x%2;
                x /= 2;
            }
            cnt_ones[i] = cnt;
        }
        return cnt_ones;
    }
};
```

### linked list cycle: 
https://leetcode.com/problems/linked-list-cycle

#### - Python Solution
```python
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        curr1 = head
        curr2 = head
        while curr2 != None and curr2.next != None:
            curr2 = curr2.next.next            
            curr1 = curr1.next
            if curr1 == curr2:
                return True
        return False
```
#### - CPP Solution
```cpp
class Solution {
public:
    bool hasCycle(ListNode *head) {
        ListNode *curr1 = head;
        ListNode *curr2 = head;
        while (curr2 != NULL and curr2->next != NULL) {
            curr2 = curr2->next->next;
            curr1 = curr1->next;
            if (curr1 == curr2)
                return true;
        }
        return false;
    }
};
```

### middle of the linked list: 
https://leetcode.com/problems/middle-of-the-linked-list

#### - Python Solution
```python
class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
        curr1 = head
        curr2 = head
        while curr2 != None and curr2.next != None:
            curr2 = curr2.next.next
            curr1 = curr1.next
        return curr1
```
#### - CPP Solution
```cpp
class Solution {
public:
    ListNode* middleNode(ListNode* head) {
        ListNode *curr1 = head;
        ListNode *curr2 = head;
        while (curr2 != NULL and curr2->next != NULL) {
            curr2 = curr2->next->next;
            curr1 = curr1->next;
        }
        return curr1;
    }
};
```

### palindrome linked list: 
https://leetcode.com/problems/palindrome-linked-list

#### - Python Solution
```python
class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        stk = []
        curr = head
        while curr != None:
            stk.append(curr.val)
            curr = curr.next
        stk = stk[::-1]
        i = 0
        curr = head
        while curr != None:
            if stk[i] != curr.val:
                return False
            curr = curr.next
            i += 1
        return True
```
#### - CPP Solution
```cpp
class Solution {
public:
    bool isPalindrome(ListNode* head) {
        vector<int> stk;
        ListNode *curr = head;
        while (curr != NULL) {
            stk.push_back(curr->val);
            curr = curr->next;
        }
        reverse(stk.begin(), stk.end());
        int i = 0;
        curr = head;
        while (curr != NULL) {
            if (stk[i] != curr->val)
                return false;
            curr = curr->next;
            i++;
        }
        return true;
    }
};
```

### remove linked list elements: 
https://leetcode.com/problems/remove-linked-list-elements

#### - Python Solution
```python
class Solution:
    def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:
        curr = head
        while curr != None and curr.next != None:
            if curr.next.val == val:
                temp = curr.next
                curr.next = curr.next.next
                del temp
            else:
                curr = curr.next
        if head != None and head.val == val:
            temp = head
            head = head.next
            del temp
        return head
```
#### - CPP Solution
```cpp
class Solution {
public:
    ListNode* removeElements(ListNode* head, int val) {
        ListNode *curr = head;
        while (curr != NULL and curr->next != NULL) {
            if (curr->next->val == val) {
                ListNode *temp = curr->next;
                curr->next = curr->next->next;
                delete temp;
            }
            else
                curr = curr->next;
        }
        if (head != NULL and head->val == val) {
            ListNode *temp = head;
            head = head->next;
            delete temp;
        }
        return head;
    }
};
```

### remove duplicates from sorted list: 
https://leetcode.com/problems/remove-duplicates-from-sorted-list

#### - Python Solution
```python
class Solution:
    def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:
        curr = head
        while curr != None and curr.next != None:
            if curr.val == curr.next.val:
                temp = curr.next
                curr.next = curr.next.next
                del temp
            else:
                curr = curr.next
        return head
```
#### - CPP Solution
```cpp
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        ListNode *curr = head;
        while (curr != NULL and curr->next != NULL) {
            if (curr->val == curr->next->val) {
                ListNode *temp = curr->next;
                curr->next = curr->next->next;
                delete temp;
            }
            else
                curr = curr->next;
        }
        return head;
    }
};
```

### reverse linked list: 
https://leetcode.com/problems/reverse-linked-list

#### - Python Solution
```python
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if head == None:
            return head
        prv = None
        cur = head
        nxt = cur.next
        while nxt != None:
            cur.next = prv
            prv = cur
            cur = nxt
            nxt = nxt.next
        cur.next = prv
        return cur
```
#### - CPP Solution
```cpp
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        if (head == NULL)
            return head;
        ListNode *prv = NULL;
        ListNode *cur = head;
        ListNode *nxt = cur->next;
        while (nxt != NULL) {
            cur->next = prv;
            prv = cur;
            cur = nxt;
            nxt = nxt->next;
        }
        cur->next = prv;
        return cur;
    }
};
```

### merge two sorted lists: 
https://leetcode.com/problems/merge-two-sorted-lists

#### - Python Solution
```python
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        if list1 == None and list2 == None:
            return None
        if list1 == None:
            return list2
        if list2 == None:
            return list1
        curr1 = list1
        curr2 = list2
        head = None
        if list1.val <= list2.val:
            head = curr1
            curr1 = curr1.next
        else:
            head = curr2
            curr2 = curr2.next
        curr = head
        while curr1 != None and curr2 != None:
            if curr1.val <= curr2.val:
                curr.next = curr1
                curr = curr.next
                curr1 = curr1.next
            else:
                curr.next = curr2
                curr = curr.next
                curr2 = curr2.next
        while curr1 != None:
            curr.next = curr1
            curr = curr.next
            curr1 = curr1.next
        while curr2 != None:
            curr.next = curr2
            curr = curr.next
            curr2 = curr2.next
        return head
```
#### - CPP Solution
```cpp
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        if (list1 == NULL and list2 == NULL)
            return NULL;
        if (list1 == NULL)
            return list2;
        if (list2 == NULL)
            return list1;
        ListNode *curr1 = list1;
        ListNode *curr2 = list2;
        ListNode *head = NULL;
        if (list1->val <= list2->val) {
            head = curr1;
            curr1 = curr1->next;
        }
        else {
            head = curr2;
            curr2 = curr2->next;
        }
        ListNode *curr = head;
        while (curr1 != NULL and curr2 != NULL) {
            if (curr1->val <= curr2->val) {
                curr->next = curr1;
                curr = curr->next;
                curr1 = curr1->next;
            }
            else {
                curr->next = curr2;
                curr = curr->next;
                curr2 = curr2->next;
            }
        }
        while (curr1 != NULL) {
            curr->next = curr1;
            curr = curr->next;
            curr1 = curr1->next;
        }
        while (curr2 != NULL) {
            curr->next = curr2;
            curr = curr->next;
            curr2 = curr2->next;
        }
        return head;
    }
};
```

### meeting rooms:
https://leetcode.com/problems/meeting-rooms

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### binary search: 
https://leetcode.com/problems/binary-search

#### - Python Solution
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        f, e = 0, len(nums)-1
        while f <= e:
            m = (f+e)//2
            if nums[m] == target:
                return m
            if nums[m] > target:
                e = m-1
            else:
                f = m+1
        return -1
```
#### - CPP Solution
```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int f = 0, e = nums.size()-1;
        while (f <= e) {
            int m = (f+e)/2;
            if (nums[m] == target)
                return m;
            if (nums[m] > target)
                e = m-1;
            else
                f = m+1;
        }
        return -1;
    }
};
```

### find smallest letter greater than target: 
https://leetcode.com/problems/find-smallest-letter-greater-than-target

#### - Python Solution
```python
class Solution:
    def nextGreatestLetter(self, letters: List[str], target: str) -> str:
        f, e = 0, len(letters)-1
        while f <= e:
            m = (f+e)//2
            if letters[m] > target:
                e = m-1
            else:
                f = m+1
        return letters[f%len(letters)]
```
#### - CPP Solution
```cpp
class Solution {
public:
    char nextGreatestLetter(vector<char>& letters, char target) {
        int f = 0, e = letters.size()-1;
        while (f <= e) {
            int m = (f+e)/2;
            if (letters[m] > target)
                e = m-1;
            else
                f = m+1;
        }
        return letters[f%letters.size()];
    }
};
```

### peak index in a mountain array: 
https://leetcode.com/problems/peak-index-in-a-mountain-array/

#### - Python Solution
```python
class Solution:
    def peakIndexInMountainArray(self, arr: List[int]) -> int:
        f, e = 0, len(arr)-1
        while f <= e:
            m = (f+e)//2
            if arr[m] < arr[m+1]:
                f = m+1
            else:
                e = m-1
        return f
```
#### - CPP Solution
```cpp
class Solution {
public:
    int peakIndexInMountainArray(vector<int>& arr) {
        int f = 0, e = arr.size()-1;
        while (f <= e) {
            int m = (f+e)/2;
            if (arr[m] < arr[m+1])
                f = m+1;
            else
                e = m-1;
        }
        return f;
    }
};
```

### average of levels in binary tree: 
https://leetcode.com/problems/average-of-levels-in-binary-tree

#### - Python Solution
```python
class Solution:
    def averageOfLevels(self, root: Optional[TreeNode]) -> List[float]:
        sums = [0] * int(1e4)
        cnts = [0] * int(1e4)

        def dfs(curr, level):
            if curr == None:
                return
            sums[level] += curr.val
            cnts[level] += 1
            dfs(curr.left, level+1)
            dfs(curr.right, level+1)

        dfs(root, 0)
        avgs = [sums[i]/cnts[i] for i in range(int(1e4)) if cnts[i] != 0]
        return avgs
```
#### - CPP Solution
```cpp
class Solution {
public:
    vector<long long> sums;
    vector<long long> cnts;

    void dfs(TreeNode* curr, int level) {
        if (curr == NULL)
            return;
        sums[level] += curr->val;
        cnts[level] ++;
        dfs(curr->left, level+1);
        dfs(curr->right, level+1);
    }
    vector<double> averageOfLevels(TreeNode* root) {
        sums.assign(1e4, 0LL);
        cnts.assign(1e4, 0LL);
        dfs(root, 0);
        vector<double> avgs;
        for (int i=0; i<1e4; i++) {
            if (cnts[i] != 0)
                avgs.push_back(1.0*sums[i]/cnts[i]);
        }
        return avgs;
    }
};
```

### minimum depth of binary tree: 
https://leetcode.com/problems/minimum-depth-of-binary-tree

#### - Python Solution
```python
class Solution:
    def minDepth(self, root: Optional[TreeNode]) -> int:
        def dfs(curr):
            if curr == None:
                return 0
            if curr.left == None:
                return dfs(curr.right)+1
            if curr.right == None:
                return dfs(curr.left)+1
            return min(dfs(curr.left), dfs(curr.right)) + 1

        return dfs(root)
```
#### - CPP Solution
```cpp
class Solution {
public:
    int dfs(TreeNode* curr) {
        if (curr == NULL)
            return 0;
        if (curr->left == NULL)
            return dfs(curr->right)+1;
        if (curr->right == NULL)
            return dfs(curr->left)+1;
        return min(dfs(curr->left), dfs(curr->right)) + 1;
    }
    int minDepth(TreeNode* root) {
        return dfs(root);
    }
};
```

### same tree: 
https://leetcode.com/problems/same-tree

#### - Python Solution
```python
class Solution:
    def isSameTree(self, p: Optional[TreeNode], q: Optional[TreeNode]) -> bool:
        def dfs(cur1, cur2):
            if cur1 == None and cur2 == None:
                return True
            if cur1 == None or cur2 == None:
                return False
            if cur1.val != cur2.val:
                return False
            return dfs(cur1.left, cur2.left) and dfs(cur1.right, cur2.right)

        return dfs(p, q)
```
#### - CPP Solution
```cpp
class Solution {
public:
    bool dfs(TreeNode* cur1, TreeNode* cur2) {
        if (cur1 == NULL and cur2 == NULL)
            return true;
        if (cur1 == NULL or cur2 == NULL)
            return false;
        if (cur1->val != cur2->val)
            return false;
        return dfs(cur1->left, cur2->left) and dfs(cur1->right, cur2->right);
    }
    bool isSameTree(TreeNode* p, TreeNode* q) {
        return dfs(p, q);
    }
};
```

### path sum: 
https://leetcode.com/problems/path-sum

#### - Python Solution
```python
class Solution:
    def hasPathSum(self, root: Optional[TreeNode], targetSum: int) -> bool:
        def dfs(curr, curr_sum):
            if curr == None:
                return curr_sum == 0
            is_valid_left = dfs(curr.left, curr_sum-curr.val)
            is_valid_right = dfs(curr.right, curr_sum-curr.val)
            if curr.right == None:
                return is_valid_left
            if curr.left == None:
                return is_valid_right
            return is_valid_left or is_valid_right

        if root == None:
            return False
        return dfs(root, targetSum)
```
#### - CPP Solution
```cpp
class Solution {
public:
    bool dfs(TreeNode* curr, int curr_sum) {
        if (curr == NULL)
            return curr_sum == 0;
        bool is_valid_left = dfs(curr->left, curr_sum-curr->val);
        bool is_valid_right = dfs(curr->right, curr_sum-curr->val);
        if (curr->right == NULL)
            return is_valid_left;
        if (curr->left == NULL)
            return is_valid_right;
        return is_valid_left or is_valid_right;
    }
    bool hasPathSum(TreeNode* root, int targetSum) {
        if (root == NULL)
            return false;
        return dfs(root, targetSum);
    }
};
```

### maximum depth of binary tree: 
https://leetcode.com/problems/maximum-depth-of-binary-tree

#### - Python Solution
```python
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        def dfs(curr):
            if curr == None:
                return 0
            return max(dfs(curr.left), dfs(curr.right)) + 1

        return dfs(root)
```
#### - CPP Solution
```cpp
class Solution {
public:
    int dfs(TreeNode* curr) {
        if (curr == NULL)
            return 0;
        return max(dfs(curr->left), dfs(curr->right)) + 1;
    }
    int maxDepth(TreeNode* root) {
        return dfs(root);
    }
};
```

### diameter of binary tree: 
https://leetcode.com/problems/diameter-of-binary-tree

#### - Python Solution
```python
class Solution:
    def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        def dfs(curr):
            if curr == None:
                return 0
            return max(dfs(curr.left), dfs(curr.right)) + 1
        
        def max_diameter(curr):
            if curr == None:
                return 0
            return max(max_diameter(curr.left), max_diameter(curr.right),
                       dfs(curr.left) + dfs(curr.right))

        return max_diameter(root)
```
#### - CPP Solution
```cpp
class Solution {
public:
    int dfs(TreeNode* curr) {
        if (curr == NULL)
            return 0;
        return max(dfs(curr->left), dfs(curr->right)) + 1;
    } 
    int max_diameter(TreeNode* curr) {
        if (curr == NULL)
            return 0;
        return max(max(max_diameter(curr->left), max_diameter(curr->right)),
                   dfs(curr->left) + dfs(curr->right));
    }
    int diameterOfBinaryTree(TreeNode* root) {
        return max_diameter(root);
    }
};
```

### merge two binary trees: 
https://leetcode.com/problems/merge-two-binary-trees

#### - Python Solution
```python
class Solution:
    def mergeTrees(self, root1: Optional[TreeNode], root2: Optional[TreeNode]) -> Optional[TreeNode]:
        def dfs(cur, cur1, cur2):
            if cur1 == None and cur2 == None:
                return None
            if cur1 == None:
                return cur2
            if cur2 == None:
                return cur1
            cur = TreeNode(cur1.val + cur2.val, TreeNode(), TreeNode())
            cur.left = dfs(cur.left, cur1.left, cur2.left)
            cur.right = dfs(cur.right, cur1.right, cur2.right)
            return cur

        root = TreeNode()
        return dfs(root, root1, root2)
```
#### - CPP Solution
```cpp
class Solution {
public:
    TreeNode* dfs(TreeNode* cur, TreeNode* cur1, TreeNode* cur2) {
        if (cur1 == NULL and cur2 == NULL)
            return NULL;
        if (cur1 == NULL)
            return cur2;
        if (cur2 == NULL)
            return cur1;
        cur = new TreeNode(cur1->val + cur2->val, new TreeNode(), new TreeNode());
        cur->left = dfs(cur->left, cur1->left, cur2->left);
        cur->right = dfs(cur->right, cur1->right, cur2->right);
        return cur;
    }
    TreeNode* mergeTrees(TreeNode* root1, TreeNode* root2) {
        TreeNode* root = new TreeNode();
        return dfs(root, root1, root2);
    }
};
```

### lowest common ancestor of a binary search tree: 
https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree

#### - Python Solution
```python
class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        def LCA(curr, p, q):
            if curr == None:
                return None
            if p < curr.val and curr.val < q:
                return curr
            if curr.val > max(p, q):
                return LCA(curr.left, p, q)
            if curr.val < min(p, q):
                return LCA(curr.right, p, q)
            return curr

        return LCA(root, p.val, q.val)
```
#### - CPP Solution
```cpp
class Solution {
public:
    TreeNode* LCA(TreeNode* curr, int p, int q) {
        if (curr == NULL)
            return NULL;
        if (p < curr->val and curr->val < q)
            return curr;
        if (curr->val > max(p, q))
            return LCA(curr->left, p, q);
        if (curr->val < min(p, q))
            return LCA(curr->right, p, q);
        return curr;
    }
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        return LCA(root, p->val, q->val);
    }
};
```

### subtree of another tree: 
https://leetcode.com/problems/subtree-of-another-tree

#### - Python Solution
```python
class Solution:
    def isSubtree(self, root: Optional[TreeNode], subRoot: Optional[TreeNode]) -> bool:
        def isSameTree(cur1, cur2):
            if cur1 == None and cur2 == None:
                return True
            if cur1 == None or cur2 == None:
                return False
            if cur1.val != cur2.val:
                return False
            return isSameTree(cur1.left, cur2.left) and isSameTree(cur1.right, cur2.right)

        def find_subtree(curr, subRoot):
            if curr == None:
                return False
            if isSameTree(curr, subRoot):
                return True
            return find_subtree(curr.left, subRoot) or find_subtree(curr.right, subRoot)

        return find_subtree(root, subRoot)
```
#### - CPP Solution
```cpp
class Solution {
public:
    bool isSameTree(TreeNode* cur1, TreeNode* cur2) {
        if (cur1 == NULL and cur2 == NULL)
            return true;
        if (cur1 == NULL or cur2 == NULL)
            return false;
        if (cur1->val != cur2->val)
            return false;
        return isSameTree(cur1->left, cur2->left) and isSameTree(cur1->right, cur2->right);
    }
    bool find_subtree(TreeNode* curr, TreeNode* subRoot) {
        if (curr == NULL)
            return false;
        if (isSameTree(curr, subRoot))
            return true;
        return find_subtree(curr->left, subRoot) or find_subtree(curr->right, subRoot);
    }
    bool isSubtree(TreeNode* root, TreeNode* subRoot) {
        return find_subtree(root, subRoot);
    }
};
```

### invert binary tree: 
https://leetcode.com/problems/invert-binary-tree

#### - Python Solution
```python
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        def dfs(curr):
            if curr == None:
                return
            curr.left, curr.right = curr.right, curr.left
            dfs(curr.left)
            dfs(curr.right)

        dfs(root)
        return root
```
#### - CPP Solution
```cpp
class Solution {
public:
    void dfs(TreeNode* curr) {
        if (curr == NULL)
            return;
        TreeNode* temp = curr->left;
        curr->left = curr->right;
        curr->right = temp;
        dfs(curr->left);
        dfs(curr->right);
    }
    TreeNode* invertTree(TreeNode* root) {
        dfs(root);
        return root;
    }
};
```

### two sum: 
https://leetcode.com/problems/two-sum

#### - Python Solution
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        idx = {}
        for i in range(len(nums)):
            idx[nums[i]] = idx.get(nums[i], [])
            idx[nums[i]].append(i)
        res = []
        for i in nums:
            if i in idx and target - i in idx:
                if i == target - i and len(idx[i]) == 1:
                    continue
                res = [idx[i][0], idx[target - i][-1]]
                break
        return res
```
#### - CPP Solution
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        map<int, vector<int>> idx;
        for (int i=0; i<nums.size(); i++)
            idx[nums[i]].push_back(i);
        vector<int> res;
        for (int i : nums) {
            if (idx.find(i) != idx.end() and idx.find(target - i) != idx.end()) {
                if (i == target - i and idx[i].size() == 1)
                    continue;
                res = {idx[i][0], idx[target - i][idx[i].size()-1]};
                break;
            }
        }
        return res;
    }
};
```

### problemname: 
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname: 
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname: 
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```

### problemname: 
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```
### problemname: 
problemlink

#### - Python Solution
```python

```
#### - CPP Solution
```cpp

```
