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