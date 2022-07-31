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
    ListNode *detectCycle(ListNode *head) {
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
