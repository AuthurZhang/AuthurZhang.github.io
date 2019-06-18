---
title: Coding Interviews 18 二叉树的镜像
date: 2019-06-06 18:50:50
tags:
- Tree
- Data Structure
- Recursion
categories: 
- Coding Interview
---
# 剑指offer 第十八题 二叉树的镜像

## 题目描述
操作给定的二叉树，将其变换为源二叉树的镜像。

<!--more-->
## 思路
Use resursion to change the left and right node.

## 代码
``` bash
    public void Mirror(TreeNode root) {
        if(root != null ){
        	//mirror the left and right
        	TreeNode temp = root.left;
        	root.left = root.right;
        	root.right = temp;
        	
        	Mirror(root.left);
        	Mirror(root.right);
        }
    }
```
