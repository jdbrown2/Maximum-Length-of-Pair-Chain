# Maximum-Length-of-Pair-Chain

Since pairs can be selected in any order, it makes it easier to have the array sorted with the first coordinate ascending.
Using dynamic programming, we can track and store the longest possible chain ending in every pair in an array `dp[]` with `pairs.length`.

We start by filling `dp[]` with all 1's because every pair has a chain of at least 1. Then, we can only add a pair to the chain if the second element of the first pair is less than the first element of the second pair, i.e. `pairs[i][1] < pairs[j][0]`. We compare every pair with every other pair (once) and if this condition is met, we store the max between the second pair's highest chain so far (`dp[j]`) and the chain we are adding this to +1 (`dp[i] + 1`).
Once we have completed all comparisons, the `max` in `dp[]` is the answer.

For example:  
`pairs = [[1,2], [2,3], [3,4], [4,5]]` 
`dp = [1, 1, 1, 1]` 

After comparison of `[1,2], [2,3]`: `dp[1, 2, 1, 1]`

`[1,2], [3,4]`: `dp[1, 2, 2, 1]`

`[1,2], [4,5]`: `dp[1, 2, 2, 2]`

`[2,3], [4,5]`: `dp[1, 2, 2, 3]`

`max(dp) = 3`
