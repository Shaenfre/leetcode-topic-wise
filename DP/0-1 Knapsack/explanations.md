## Last Stone Weight 2
- Trick is to divide the stones into almost 2 equal subsets
- so that their difference gets minimum
- so find stone sum so that it is less than equal to half the sum of stones weight using 0-1 Knapsack (either pick the stone at index i or don't)
- dp(index, current_wt)
### Similar problem
- Target Sum
- Partition Equal Subset Sum