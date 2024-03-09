
* Word Wrap: Dynamic Programming

```java

class Solution {
    public int solveWordWrap(int[] nums, int k) {

        int[][] dp = new int[nums.length+1][k + 1];
        for (int[] a : dp)
            Arrays.fill(a, -1);
        
        return helper(nums, nums.length, k, 0, k, dp);
    }

    private int helper(int[] words, int n, int k, int wordIdx, int remLen, int[][] dp) {
        
        if (wordIdx == n - 1) {
            dp[wordIdx][remLen] = words[wordIdx] < remLen ? 0 : remLen * remLen;
            return dp[wordIdx][remLen];
        }

        if (dp[wordIdx][remLen] != -1) 
            return dp[wordIdx][remLen];
            
    
        int curWordLen = words[wordIdx];
        
        // If word can fit on the same line
        int sameLineCost = Integer.MAX_VALUE;
        
        if (remLen == k || curWordLen < remLen) {
            sameLineCost = helper(words, n, k, wordIdx + 1, 
            remLen == k ? remLen - curWordLen : remLen - curWordLen - 1, dp);
        }
        
        int nextLineCost = remLen * remLen + helper(words, n, k,
        wordIdx + 1, k - curWordLen, dp);
        
        dp[wordIdx][remLen] = Math.min(sameLineCost, nextLineCost);
        
        return dp[wordIdx][remLen];
    }
}
```


