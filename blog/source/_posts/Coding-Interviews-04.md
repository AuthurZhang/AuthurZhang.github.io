---
title: Coding_Interviews_04
date: 2019-06-04 15:18:45
tags:
- Tree
- Data Structure
categories: 
- Coding Interview
---

# 剑指offer 第四题 重建二叉树

## 题目描述
输入某二叉树的前序遍历和中序遍历的结果，请重建出该二叉树。假设输入的前序遍历和中序遍历的结果中都不含重复的数字。例如输入前序遍历序列{1,2,4,7,3,5,6,8}和中序遍历序列{4,7,2,1,5,3,8,6}，则重建二叉树并返回。

<!--more-->
## 思路
Search, divide and use recursion
## 代码
``` bash
    class TreeNode {
        int val = 0;
        TreeNode left = null;
        TreeNode right = null;

        public TreeNode(int val) {
            this.val = val;
        }
    }

    /**
     * 根据前序遍历，中序遍历重建二叉树
     * @param pre
     * @param in
     * @return
     */
    public TreeNode reConstructBinaryTree(int [] pre,int [] in) {

        return reConBTree(pre,0,pre.length-1,in,0,in.length-1);

    }

    public TreeNode reConBTree(int[] pre,int preleft,int preright,int[] in,int inleft,int inright){
        if(preleft > preright || inleft> inright)//递归结束条件 到达边界
            return null;
        //新建一个TreeNode
        TreeNode pRootOfTree = new TreeNode(pre[preleft]);
        //对中序数组进行遍历 找到根节点，划分，递归
        for(int i = inleft; i<= inright; i++){
            if(pre[preleft] == in[i]){
                //重构左子树递归
                pRootOfTree.left = reConBTree(pre,preleft+1,preleft+i-inleft,in,inleft,i-1);
                //重构右子树,递归
                pRootOfTree.right = reConBTree(pre,preleft+i+1-inleft,preright,in,i+1,inright);
            }
        }
        return pRootOfTree;
    }

    /**
    * 中序后序遍历重建树 
    * @Title: reConstructBinaryTree1
    * @Description: TODO
    * @param @param post
    * @param @param in
    * @param @return
    * @return TreeNode
     */
    public static TreeNode reConstructBinaryTree1(char [] post,char [] in){
    	return reConBTree1(post,0,post.length-1,in,0,in.length-1);
    }
    
    public static TreeNode reConBTree1(char[] post,int postleft,int postright,char[] in,int inleft,int inright){
        if(postleft > postright || inleft> inright){//递归结束条件 到达边界
        	 return null;
        }
           
        //新建一个TreeNode
        TreeNode pRootOfTree = new TreeNode(post[postright]);
        //对中序数组进行遍历 找到根节点，划分，递归
        for(int i = inleft; i<= inright; i++){
            if(post[postright] == in[i]){
                //重构左子树递归
                pRootOfTree.left = reConBTree1(post,postleft, i-1 ,in,inleft,i-1);
                //重构右子树,递归
                pRootOfTree.right = reConBTree1(post,i,postright-1,in,i+1,inright);
                
            }
        }
        return pRootOfTree;     
    }
```
