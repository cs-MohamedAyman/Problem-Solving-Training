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
        def dp(n: int) -> int:
            if n < 2 :
                return 1
            if self.memo[n] != -1:
                return self.memo[n]
            self.memo[n] = dp(n-1) + dp(n-2)
            return self.memo[n]

        self.memo = [-1] * 46
        return dp(n)
```
```cpp
class Solution {
public:
    vector<int> memo;
    int dp(int n) {
        if (n < 2)
            return 1;
        if (memo[n] != -1)
            return memo[n];
        memo[n] = dp(n-1) + dp(n-2);
        return memo[n];
    }
    int climbStairs(int n) {
        memo.assign(46, -1);
        return dp(n);
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
