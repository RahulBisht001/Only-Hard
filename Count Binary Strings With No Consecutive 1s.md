
## Count Binary Strings With No Consecutive 1s

watch videa explantion for matrix exponation log(N) complexity 
https://www.youtube.com/watch?v=GgxgfmHbXYw
```java
class Solution {
    
    int mod = 1000000007;
    
    public int countStrings(long n) {
        
        // 1. Recursion O(2^N)
        // 2. Memoization O(N*M) with recursive stack and other is tabulation
        // 3. Space otimized (1) space with O(N) TC
        
       // 4. how to solve it in (log(N))
       
       // that is via matrix exponantiation 
       // watch video https://www.youtube.com/watch?v=GgxgfmHbXYw
        
        int ans = (int)fibo(n + 2);
        return ans;
    }
    
    public long fibo(long n){
        
        long[][] F = {{1,1},{1,0}};
        
        if(n == 0)
            return 0;
            
        power(F,n-1);
            
        return F[0][0];
    }
    public void power(long[][] F ,long n){
        
        if(n == 0 || n == 1){
            return;
        }
        
        long[][] M = {{1,1},{1,0}};
    
    
        power(F , n/2);
        multiplyMatrix(F , F);
        
        if( n % 2 != 0){
            multiplyMatrix(F , M);
        }
    }
    public void multiplyMatrix(long[][]F ,long[][]M){
        
        // M is already defined
        
        long x = ( (F[0][0] % mod *M[0][0] % mod) % mod +
            (F[0][1] % mod * M[1][0] % mod) % mod ) % mod;
                      
        long y = ( (F[0][0] % mod *M[0][1] % mod) % mod + 
            (F[0][1] % mod * M[1][1] % mod) % mod ) % mod;
                    
        long z = ( (F[1][0] % mod *M[0][0] % mod) % mod +
            (F[1][1] % mod * M[1][0] % mod) % mod ) % mod;
            
        long w = ( (F[1][0] % mod *M[0][1] % mod) % mod + 
            (F[1][1] % mod * M[1][1] % mod) % mod ) % mod;
        
        
        F[0][0] = x;
        F[0][1] = y;
        F[1][0] = z;
        F[1][1] = w;
    }
    
}

```
