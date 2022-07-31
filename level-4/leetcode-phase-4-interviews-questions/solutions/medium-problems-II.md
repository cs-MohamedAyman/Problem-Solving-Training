<img align="right" width="80" src="https://github.com/cs-MohamedAyman/Problem-Solving-Training/blob/master/online-judges-logos/leetcode.jpg">

## LeetCode OJ - Phase 4 Interviews Questions - Medium Problems II

### partition equal subset sum:
Problem Link: https://leetcode.com/problems/partition-equal-subset-sum

#### - Python Solution
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
#### - CPP Solution
```cpp
class Solution {
public:
    bool canPartition(vector<int>& nums) {
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

### partition to k equal sum subsets:
Problem Link: https://leetcode.com/problems/partition-to-k-equal-sum-subsets

#### - Python Solution
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

#### - CPP Solution
```cpp
class Solution {
    bool check_partitions(int i, int k, int curr_total,
                          const int &target, const vector<int>& nums, bool visited[]) {
        if (k == 0)
            return true;
        if (curr_total > target)
            return false;
        if (curr_total == target)
            return check_partitions(0, k-1, 0, target, nums, visited);
        for (int j=i; j<nums.size(); j++) {
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
    bool canPartitionKSubsets(vector<int>& nums, int k) {
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

### best time to buy and sell stock with cooldown:
Problem Link: https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown

#### - Python Solution
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
#### - CPP Solution
```cpp
class Solution {
    int memo[5003][2];
    int dp(int i, bool buy, const vector<int>& prices) {
        if (i >= prices.size())
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
    int maxProfit(vector<int>& prices) {
        memset(memo, -1, sizeof memo);
        return dp(0, 1, prices);
    }
};
```

### linked list cycle ii:
Problem Link: https://leetcode.com/problems/linked-list-cycle-ii

#### - Python Solution
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
#### - CPP Solution
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

### add two numbers:
Problem Link: https://leetcode.com/problems/add-two-numbers

#### - Python Solution
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
#### - CPP Solution
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

### remove nth node from end of list:
Problem Link: https://leetcode.com/problems/remove-nth-node-from-end-of-list

#### - Python Solution
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
#### - CPP Solution
```cpp
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode *head, int n) {
        ListNode *res = new ListNode(0, head);
        ListNode *curr1 = res;
        ListNode *curr2 = head;
        while (n) {
            curr2 = curr2->next;
            n -= 1;
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

### sort list:
Problem Link: https://leetcode.com/problems/sort-list

#### - Python Solution
```python
class Solution:
    def sortList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        def middleNode(head):
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
            right = middleNode(head)
            temp = right.next
            right.next = None
            right = temp
            left  = merge_sort(left)
            right = merge_sort(right)
            return mergeTwoLists(left, right)
            
        return merge_sort(head)
```
#### - CPP Solution
```cpp
class Solution {
    ListNode* middleNode(ListNode *head) {
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
            ListNode *right = middleNode(head);
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

### reorder list:
Problem Link: https://leetcode.com/problems/reorder-list/

#### - Python Solution
```python
class Solution:
    def reorderList(self, head: Optional[ListNode]) -> None:
        def middleNode(head):
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

        mid = middleNode(head)
        temp = mid.next
        mid.next = None
        mid = temp
        mid = reverseList(mid)
        head = mergeTwoLists(head, mid)
        return head
```
#### - CPP Solution
```cpp
class Solution {
    ListNode* middleNode(ListNode *head) {
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
        ListNode *mid = middleNode(head);
        ListNode *temp = mid->next;
        mid->next = NULL;
        mid = temp;
        mid = reverseList(mid);
        head = mergeTwoLists(head, mid);
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
