---
title: Coding Interviews 26 二叉搜索树与双向链表
date: 2019-06-08 15:51:33
tags:
- Tree
- LinkedList
- Data Structure
categories: 
- Coding Interview
---
# 剑指offer 第二十六题 二叉搜索树与双向链表

## 题目描述
输入一棵二叉搜索树，将该二叉搜索树转换成一个排序的双向链表。要求不能创建任何新的结点，只能调整树中结点指针的指向。

<!--more-->
## 思路
use mid iteration and then put into a list.

## 代码
``` bash
    /**
     * 中序遍历 然后制成链表
     * @param pRootOfTree
     * @return
     */
    public TreeNode Convert(TreeNode pRootOfTree) {

        if(pRootOfTree == null){
            return null;
        }

        //mid and put into the list
        ArrayList<TreeNode> treeNodes = new ArrayList<>();
        midIteration(pRootOfTree,treeNodes);

        //link the list
        TreeNode pre = null;
        for(int i = 0; i < treeNodes.size(); i++){
            treeNodes.get(i).left = pre;
            pre = treeNodes.get(i);
            if(i< treeNodes.size()-1){
                treeNodes.get(i).right = treeNodes.get(i+1);

            }else {
                treeNodes.get(i).right = null;
            }
        }
        return treeNodes.get(0);

    }

    public void midIteration(TreeNode root, ArrayList<TreeNode> treeNodes){
        if(root != null){
            midIteration(root.left,treeNodes);
            treeNodes.add(root);
            midIteration(root.right,treeNodes);
        }
    }
```
