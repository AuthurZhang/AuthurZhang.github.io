---
title: Coding Interviews 14 链表倒数第k个节点
date: 2019-06-05 18:50:24
tags:
- LinkedList
- Stack
- Data Structure
categories: 
- Coding Interview
---
# 剑指offer 第十四题 链表倒数第k个节点

## 题目描述
输入一个链表，输出该链表中倒数第k个结点。

<!--more-->
## 思路
Put the ListNode into a stack.
Find the k ListNode from a stack.

## 代码
``` bash
    /*
    public class ListNode {
        int val;
        ListNode next = null;

        ListNode(int val) {
            this.val = val;
        }
    }*/
    public class Solution {

        public ListNode FindKthToTail(ListNode head,int k) {

            ListNode p = head;
            //first time : get length from start to end
            int count = 0;
            while(p!=null){
                count++;
                p = p.next;
            }

            //second time : find k
            ListNode result = head;
            if(count-k<0){
                return null;
            }
            for(int i = 0; i< count-k; i++){
                result = result.next;
            }
            return result;
        }
    }
```
