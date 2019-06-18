---
title: Coding Interviews 17 树的子结构
date: 2019-06-06 15:50:44
tags:
- Tree
- Data Structure
categories: 
- Coding Interview
---
# 剑指offer 第十七题 树的子结构

## 题目描述
输入两棵二叉树A，B，判断B是不是A的子结构。（ps：我们约定空树不是任意一个树的子结构）

<!--more-->
## 思路
Two Recursion:
1. Find in Tree 1 if there is a tree node in Tree 1 equal to the root of Tree 2
2. In this case, compare the every node in Tree 2 with Tree1, and then return the result.

## 代码
``` bash
    /**
    public class TreeNode {
        int val = 0;
        TreeNode left = null;
        TreeNode right = null;

        public TreeNode(int val) {
            this.val = val;

        }

    }
    */
    public class Solution {
        
        public boolean HasSubtree(TreeNode root1,TreeNode root2) {
            boolean result = false;
            if(root1 != null && root2 != null){
                if(root1.val == root2.val){
                result = ifRoot1HasRoot2(root1,root2); 
                }
                //find in left node
                if(!result){
                    result = HasSubtree(root1.left,root2);
                }
                //find in right node
                if(!result){
                    result = HasSubtree(root1.right,root2);
                }
            }
            return result;
        }
        
        public boolean ifRoot1HasRoot2(TreeNode root1,TreeNode root2){
            boolean result = false;
            if(root2 == null){
                result = true;
            }
            if(root1 != null && root2!= null){
                if(root1.val == root2.val){
                    result = ifRoot1HasRoot2(root1.left,root2.left)
                        &&ifRoot1HasRoot2(root1.right,root2.right);
                }else{
                    result = false;
                }
            }
            
            return result;
        }
        
    }
```
