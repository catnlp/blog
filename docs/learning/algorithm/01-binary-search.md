<h1 style="text-align:center">二分查找</h1>

## 原理

### 问题

在排序数组中，查找目标值。

### 方法

比较中间值和目标值，如果不相等，则将问题空间缩小一半，再进行搜索。

## 模板

### 查找目标值

```python
def binary_search(nums, target):
    left = 0
    n = len(nums)
    right = n - 1
    while left <= right:
        mid = left + (right - left) // 2
        val = nums[mid]
        if val == target:
            return mid
        elif val < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1
```


### 查找左边界

```python
def left_bound(nums, target):
    left = 0
    n = len(nums)
    right = n - 1
    while left <= right:
        mid = left + (right - left) // 2
        val = nums[mid]
        if val < target:
            left = mid + 1
        else:
            right = mid - 1  # 相等情况，收缩右边界
    if left >= n or nums[left] != target:
        return -1
    return left
```

### 查找右边界

```python
def right_bound(nums, target):
    left = 0
    n = len(nums)
    right = n - 1
    while left <= right:
        mid = left + (right - left) // 2
        val = nums[mid]
        if val <= target:
            left = mid + 1  # 相等情况，收缩左边界
        else:
            right = mid - 1
    if right < 0 or nums[right] != target:
        return -1
    return right
```

## 例题

