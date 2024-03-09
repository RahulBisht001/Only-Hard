
* There are 3 solutions

  1. we have 2 sorted arrays, so we can use another array of `n + m` length and sort them.
     It will take O(N + M) time complexity but O(N+M) space complexity.

  2. another method is :
    start from the end of the first array and the start of the first array and then swap if there is a greater
    element in the left array and once the loop breaks we will have the correct element in each array.
    although they will be rearranged and we can correct their order by the sort method,here the space complexity
    will be O(1).


     ```java
     import java.util.*;
     
     public class Solution {
        public static void mergeTwoSortedArraysWithoutExtraSpace(
                long[] arr1, long[] arr2) {
  
          int left = arr1.length - 1;
          int right = 0;
  
          while (left >= 0 && right <= arr2.length) {
              if (arr1[left] > arr2[right]) {
                  long temp = arr1[left];
                  arr1[left] = arr2[right];
                  arr2[right] = temp;
  
                  left--;
                  right++;
              } else
                  break;
          }
  
          Arrays.sort(arr1);
          Arrays.sort(arr2);
      }
    }
  ```



3. the third and most optimal method is the gap method. this is derived from a sorting technique called shell sort.
