---
title: Coding Interviews 22 打印二叉树
date: 2019-06-07 16:51:15
tags:
- Tree
- Data Structure
categories: 
- Coding Interview
---
# 剑指offer 第二十二题 打印二叉树

## 题目描述
从上往下打印出二叉树的每个节点，同层节点从左至右打印。

<!--more-->
## 思路
It is like BFS, use queue.
Tips: DFS, use stack or recursion.

## 代码
``` bash
    public ArrayList<Integer> PrintFromTopToBottom(TreeNode root) {

        ArrayList<Integer> result = new ArrayList<>();
        Queue<TreeNode> queue = new LinkedList<>();

        if(root != null){
            queue.add(root);
        }

        while (!queue.isEmpty()){
            TreeNode temp = queue.poll();
            result.add(temp.val);
            if(temp.left!=null){
                queue.add(temp.left);
            }
            if(temp.right!=null){
                queue.add(temp.right);
            }
        }
        return result;

    }

```
