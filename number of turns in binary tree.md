
## Number of Turn in a Binary Tree

* This question is a follow-up question of the LCA of Nodes in the Binary tree.
* Once you get the LCA than you have to check for the turn in the nodes.

```java
class Solution {
    
    static int Count;
    static int NumberOfTurns(Node root, int first, int second) {
        
        
        //Find the LCA of nodes
        Node LCA = findLCA(root, first, second);
        
        if (LCA == null)
            return -1;
            
        Count = 0;
 
        
        if (LCA.data != first && LCA.data != second) {
            
            // count number of turns needs to reached 
            // the first node from LCA
            if (CountTurn(LCA.left, first, true)
                || CountTurn(LCA.right, first, false));
 
            // count number of turns needs to reached
            // the second node from LCA
            if (CountTurn(LCA.right, second, false)
                || CountTurn(LCA.left, second, true));
            
            return Count + 1;
        }
 
       
        // count number of turns needs to reach 
        // the second node from LCA
        if (LCA.data == first) {
            CountTurn(LCA.left, second, true);
            CountTurn(LCA.right, second, false);
            
            return Count;
        } 
        else {
            // count number of turns needs to reached
            // the first node from LCA1 
            CountTurn(LCA.left, first, true);
            CountTurn(LCA.right, first, false);
            
            return Count;
        }
    }
    
    static Node findLCA(Node root, int n1, int n2) {
       
        if (root == null)
            return null;
        if (root.data == n1 || root.data == n2)
            return root;
       
        Node left_lca = findLCA(root.left, n1, n2);
        Node right_lca = findLCA(root.right, n1, n2);
       
        if (left_lca != null && right_lca != null)
            return root;
 
        return (left_lca != null) ? left_lca : right_lca;
    }
    
    static boolean CountTurn(Node root,int key, boolean turn) {
        
        if (root == null)
            return false;
        if (root.data == key)
            return true;
 
        if (turn == true) {
            if (CountTurn(root.left, key, turn))
                return true;
            if (CountTurn(root.right, key, !turn)) {
                Count += 1;
                return true;
            }
        } 
        else{
            if (CountTurn(root.right, key, turn))
                return true;
            if (CountTurn(root.left, key, !turn)) {
                Count += 1;
                return true;
            }
        }
        
        return false;
    }

}
```
