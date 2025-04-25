## Shortest common supersequence
- The trick is to find the LCS this will be the thing which will repeat
only once and not from both string
- while finding the lcs record the index which resulted in maximum length

```python
class Solution:
    def shortestCommonSupersequence(self, str1: str, str2: str) -> str:
        SAME = 0
        ADD_S1 = 1
        ADD_S2 = 2

        N1, N2 = len(str1), len(str2)

        nxt = [[None] * N2 for _ in range(N1)]

        @cache
        def dp(i1, i2):
            if i1 == len(str1) or i2 == len(str2): return 0

            best = -1

            if str1[i1] == str2[i2]: 
                v = 1 + dp(i1 + 1, i2 + 1)
                if v > best:
                    nxt[i1][i2] = SAME
                    best = v

            v = dp(i1 + 1, i2)

            if v > best:
                nxt[i1][i2] = ADD_S1
                best = v

            v = dp(i1, i2 + 1)

            if v > best:
                nxt[i1][i2] = ADD_S2
                best = v

            return best

        ans = []

        dp(0, 0)

        i1, i2 = 0, 0

        print(nxt)

        while i1 < N1 and i2 < N2:
            match nxt[i1][i2]:
                case 0:
                    ans.append(str1[i1])
                    i1 += 1
                    i2 += 1
                case 1:
                    ans.append(str1[i1])
                    i1 += 1
                case 2:
                    ans.append(str2[i2])
                    i2 += 1
                case _:
                    assert(False)
        
        while i1 < N1:
            ans.append(str1[i1])
            i1 += 1

        while i2 < N2:
            ans.append(str2[i2])
            i2 += 1

        return "".join(ans)
```

## Delete operations for two strings 
TODO