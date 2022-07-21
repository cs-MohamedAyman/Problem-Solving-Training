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

### remove linked list elements: 
https://leetcode.com/problems/remove-linked-list-elements

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

### binary search: 
https://leetcode.com/problems/binary-search

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

Python Solution 
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
CPP Solution 
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

### problemname: 
problemlink

Python Solution ```python

```
CPP Solution ```cpp

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
