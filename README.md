# Inorder Successor in BST
## https://leetcode.com/problems/inorder-successor-in-bst

Given a binary search tree and a node in it, find the in-order successor of that node in the BST.

The successor of a node p is the node with the smallest key greater than p.val.

**Note:**
1. If the given node has no in-order successor in the tree, return null.
2. It's guaranteed that the values of the tree are unique.

# Implementation :

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public TreeNode inorderSuccessor(TreeNode root, TreeNode p) {
        List<TreeNode> inorder = new ArrayList<>();
        helper(root,inorder);
        for(TreeNode node : inorder){
            if(node.val > p.val)
                return node;
        }
        return null;
    }
    
    public void helper(TreeNode root, List<TreeNode> list){
        if(root != null){
            helper(root.left, list);
            list.add(root);
            helper(root.right, list);
        }
    }
}
```
