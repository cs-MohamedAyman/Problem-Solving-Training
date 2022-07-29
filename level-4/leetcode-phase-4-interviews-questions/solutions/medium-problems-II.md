<img align="right" width="80" src="https://github.com/cs-MohamedAyman/Problem-Solving-Training/blob/master/online-judges-logos/leetcode.jpg">

## LeetCode OJ - Phase 4 Interviews Questions - Medium Problems I

### Partition Equal Subset Sum:
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
                if visised[j]:
                    continue
                visised[j] = True
                if check_partitions(j+1, k, curr_total+nums[j]):
                    return True
                visised[j] = False
            return False

        nums_sum = sum(nums)
        if nums_sum % k:
            return False
        target = nums_sum // k
        nums.sort(reverse=True)
        visised = [0] * len(nums)
        return check_partitions(0, k, 0)
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
