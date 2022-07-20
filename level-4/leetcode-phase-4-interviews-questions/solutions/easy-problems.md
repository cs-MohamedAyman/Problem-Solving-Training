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
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

### problemname: problemlink

```python
```
```cpp
```

