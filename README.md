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
## Can we do better : 🤔

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
        // case 1 : when p have a right node, we start from right of p
         if(p.right != null){
             return findMinimum(p.right);
         }
        // case 2 : when p doesn't have right node, we start from root
        TreeNode inorderSuccessor = null;
        while(root != null){
            if(root.val > p.val){
                inorderSuccessor = root;
                root = root.left;
            } else if(root.val < p.val){
                root = root.right;
            } else {
                break;
            }
        }
        return inorderSuccessor;
    }
    
    private TreeNode findMinimum(TreeNode root){
        while(root.left != null)
            root = root.left;
        return root;
    }
}

```

# References :
1. https://www.youtube.com/watch?v=kdK_5rl1cVw
2. https://leetcode.com/articles/inorder-successor-in-bst
3. https://www.youtube.com/watch?v=5cPbNCrdotA
