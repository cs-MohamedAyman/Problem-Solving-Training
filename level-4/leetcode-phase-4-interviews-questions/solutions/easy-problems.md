<img align="right" width="80" src="https://github.com/cs-MohamedAyman/Problem-Solving-Training/blob/master/online-judges-logos/leetcode.jpg">

## LeetCode OJ - Phase 4 Interviews Questions - Easy Problems


### contains duplicate: https://leetcode.com/problems/contains-duplicate

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

### missing number: https://leetcode.com/problems/missing-number

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

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

### problemname : problemlink

```python
```
```cpp
```

