<h1 style="text-align:center">字符串</h1>


## 匹配

### KMP

PMT中的值是字符串的前缀集合与后缀集合的交集中最长元素的长度

```python
def kmp(s: str, p: str) -> int:
    s_size = len(s)
    p_size = len(p)
    if s_size < p_size:
        return -1

    next_step = get_next(p)
    i = j = 0
    while i < s_size and j < p_size:
        if j == -1 or s[i] == p[j]:
            i += 1
            j += 1
        else:
            j = next_step[j]

    if j == p_size:
        return i - p_size
    return -1


def get_next(p):
    i = 1
    j = 0
    next_list = [0] * (len(p) + 1)
    next_list[0] = -1
    while i < len(p):
        if j == -1 or p[i] == p[j]:
            j += 1
            i += 1
            next_list[i] = j
        else:
            j = next_list[j]
    return next_list


if __name__ == "__main__":
    s1 = "helalalbo"
    s2 = "lalb"
    print(kmp(s1, s2))
```
