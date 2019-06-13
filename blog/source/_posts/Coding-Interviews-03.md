---
title: Coding Interviews 03 倒序打印链表
date: 2019-06-03 23:35:52
tags:
---
<!--more-->
# 剑指offer 第三题 倒序打印链表

## 题目描述
输入一个链表，按链表值从尾到头的顺序返回一个ArrayList。
## 思路
use stack
## 代码
``` bash
    public static ArrayList<Integer> printListFromTailToHead(ListNode listNode) {
        Stack<Integer> stack = new Stack<Integer>();
        ArrayList<Integer> result = new ArrayList<Integer>();
        //push into stack
        while(listNode!=null){
            stack.push(listNode.val);
            listNode = listNode.next;
        }
        //pop and push into list
        while (!stack.isEmpty()){
            result.add(stack.pop());
        }
        return result;
    }
```