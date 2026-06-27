Premium

### Python
```py
class Solution:
    MOD = 10 ** 9 + 7

    def powerUpdate(self, nums: list[int], p: int, queries: list[list[int]]) -> list[int]:
        result = []
        arr = SortedList(nums)
        for q, k in queries:
            arr.add(q)
            p = pow(p, arr[-k], self.MOD)
            result.append(p)
        return result
```