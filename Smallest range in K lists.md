## Smallest range in K lists

```java

class Solution {
	static int[] findSmallestRange(int[][] KSortedArray,int n,int k) {
	    
	    int[] res = { -100000, 100000 };
	    int max = Integer.MIN_VALUE;
	    
	    PriorityQueue<int[]>pq = new PriorityQueue<>((a,b)->a[0]-b[0]);
	    
	    for(int i = 0; i < k;++i){
	        int minOfList = KSortedArray[i][0];
	        max = Math.max(max , minOfList);
	        
	        pq.add(new int[]{minOfList,0,i});
	    }
	    
	    while(true){
	        int[]min_arr = pq.poll();
	        
	        if(res[1] - res[0] > max - min_arr[0]){
	            res[1] = max;
	            res[0] = min_arr[0];
	        }
	        
	        min_arr[1]++;
	   
	        int[]curr = KSortedArray[min_arr[2]];
	        
	        if(min_arr[1] == curr.length)
	            break;
	        else{
	            max = Math.max(max ,curr[min_arr[1]]);
	            min_arr[0] = curr[min_arr[1]];
	            pq.add(min_arr);
	        }
	    }
	    
	    return res;
	}
}
```
