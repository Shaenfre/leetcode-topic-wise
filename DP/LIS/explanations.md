## Russian Doll Envelopes

- Sort the envelopes by e[0], -e[1]
- So if e[1] at pos j > e[1] at position i (j > i) 
- e[0] will automatically be greater (since it is sorted)
- so find LIS on e[1] that will be the answer

```python
class Solution:
    def maxEnvelopes(self, envelopes: List[List[int]]) -> int:
        envelopes.sort(key = lambda e: (e[0], -e[1]))
        longest = []
        print(envelopes)

        for _, h in envelopes:
            idx = bisect_left(longest, h)

            if idx >= len(longest):
                longest.append(h)
            else:
                longest[idx] = h

        return len(longest)

```

## Number of longest increasing subsequence

- Find LIS using n**2 algorithm
- Maintain one other array count (stores count of LIS till now)

```python
for i in range(len(nums)):
    for j in range(i):
        if nums[i] > nums[j]:
            if lis[j] + 1 > lis[i]:
                lis[i] = lis[j] + 1
                count[i] = count[j]
            elif lis[j] + 1 == lis[i]:
                count[i] += count[j]

mx = max(list)
return sum(x for index, x in enumerate(count) if lis[index] == mx)

```