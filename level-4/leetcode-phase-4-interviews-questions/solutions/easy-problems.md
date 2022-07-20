<img align="right" width="80" src="https://github.com/cs-MohamedAyman/Problem-Solving-Training/blob/master/online-judges-logos/leetcode.jpg">

## LeetCode OJ - Phase 4 Interviews Questions - Easy Problems

### contains duplicate: 
https://leetcode.com/problems/contains-duplicate

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        return len(nums) != len(set(nums))
```
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

```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        n = len(nums)
        return n*(n+1)//2 - sum(nums)
```
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

```python
class Solution:
    def climbStairs(self, n: int) -> int:
        memo = [0] * 46
        memo[0] = memo[1] = 1
        for i in range(2, n+1):
            memo[i] = memo[i-1] + memo[i-2]
        return memo[n]
```
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

### problemname: 
problemlink

```python

```
```cpp

```

### problemname: 
problemlink

```python

```
```cpp

```

### problemname: 
problemlink

```python

```
```cpp

```

### problemname: 
problemlink

```python

```
```cpp

```

### problemname: 
problemlink

```python

```
```cpp

```

### problemname: 
problemlink

```python

```
```cpp

```

### problemname: 
problemlink

```python

```
```cpp

```

### problemname: 
problemlink

```python

```
```cpp

```

### problemname: 
problemlink

```python

```
```cpp

```

### problemname: 
problemlink

```python

```
```cpp

```

### problemname: 
problemlink

```python

```
```cpp

```

### problemname: 
problemlink

```python

```
```cpp

```

### problemname: 
problemlink

```python

```
```cpp

```

### problemname: 
problemlink

```python

```
```cpp

```

### problemname: 
problemlink

```python

```
```cpp

```
