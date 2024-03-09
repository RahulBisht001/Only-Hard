```java

class Solution { 
    long smallestpositive(long[]nums, int n){ 
        
        long res = 1;
        
        Arrays.sort(nums);
        
        for(int i = 0;i < n;++i){
            if(nums[i] <= res)
                res += nums[i];
            else
                break;
        }
        return res;
        
    }
} 
```
