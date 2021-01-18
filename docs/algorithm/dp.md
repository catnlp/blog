<h2 style="text-align:center">动态规划</h1>

### 💡思路

> **找到【状态】和【选择】->明确dp数组/函数的定义->寻找【状态】之间的关系**

### 📝题目

#### 最长递增子序列

> 输入一个无序的整数数组，找到其中最长递增子序列的长度。

```python
def len_lis(nums):
    result = 0
    dp = [1] * len(nums)
    for i, num in enumerate(nums):
        for j in range(i):
            if nums[i] >= nums[j]:
                dp[i] = max(dp[i], dp[j] + 1)
        if dp[i] > result:
            result = dp[i]
    return result
```
