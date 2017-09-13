---
layout: post
title:  "算法题：合并二叉树"
date:   2017-09-13 00:57:00 +0800
categories: jekyll update
---
给出2个二叉树，要求进行合并，具体要求如下：

Given two binary trees and imagine that when you put one of them to cover the other, some nodes of the two trees are overlapped while the others are not.

You need to merge them into a new binary tree. The merge rule is that if two nodes overlap, then sum node values up as the new value of the merged node. Otherwise, the NOT null node will be used as the node of new tree.

Example: 

```
Input: 
	Tree 1                     Tree 2                  
          1                         2                             
         / \                       / \                            
        3   2                     1   3                        
       /                           \   \                      
      5                             4   7                  
Output: 
Merged tree:
	     3
	    / \
	   4   5
	  / \   \ 
	 5   4   7
```

Solution 1: Recurtion (*by Java*)

思路：每次只合并当前节点，然后将左右子树分别递归。对于有n个节点的二叉树，时间复杂度为O(n)

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
		// recursion
		public TreeNode mergeTrees(TreeNode t1, TreeNode t2) {
	    	if (t1 == null)
	        	return t2;
	    	if (t2 == null)
	        	return t1;
	    	t1.val = t1.val + t2.val;
	    	t1.left = mergeTrees(t1.left, t2.left);
	    	t1.right = mergeTrees(t1.right, t2.right);
	    	return t1;
		}
	}
	
Solution2: Iteration(*by java*)
思路：借用stack的特性，将未合并节点放入stack，在合并stack顶部元素的同时，将其子树也放入stack。迭代直至stack为空。

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
    	// iteration
	    public TreeNode mergeTrees(TreeNode t1, TreeNode t2) {
	        if (t1 == null) {
	            return t2;
	        }
	        Stack<TreeNode[]> stack = new Stack<TreeNode[]>();
	        TreeNode[] tn = { t1, t2 };
	        stack.push(tn);
	        while(!stack.empty()) {
	            TreeNode[] t = stack.pop();
	            if (t[0] == null || t[1] == null) {
	                continue;
	            }
	            t[0].val += t[1].val;
	            if (t[0].left == null) {
	                t[0].left = t[1].left;
	            } else {
	                stack.push(new TreeNode[] { t[0].left, t[1].left });
	            }
	            if (t[0].right == null) {
	                t[0].right = t[1].right;
	            } else {
	                stack.push(new TreeNode[] { t[0].right, t[1].right });
	            }
	        }
	        return t1;
	    }
	}
	

总结：在本题中，在时间复杂度相同的情况下，递归更加简洁，容易理解。