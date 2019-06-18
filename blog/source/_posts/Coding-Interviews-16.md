---
title: Coding Interviews 16 合并排序的列表
date: 2019-06-06 13:50:37
tags:
- LinkedList
- Data Structure
- Recursion
categories: 
- Coding Interview
---
# 剑指offer 第十六题 合并排序的列表

## 题目描述
输入两个单调递增的链表，输出两个链表合成后的链表，当然我们需要合成后的链表满足单调不减规则。

<!--more-->
## 思路
see leetcode, add two sort array.

## 代码
``` bash
    public ListNode Merge(ListNode list1,ListNode list2) {
        if(list1 == null){
        	return list2;
        }
        if(list2 == null){
        	return list1;
        }
        if(list1 != null && list2 != null){
        	
        	ListNode result;
        	ListNode next;
        	//compare which one is small
        	if(list1.val <= list2.val){
        		
        		result = list1;
        		next = list1.next;
        		result.next = Merge(next, list2);
        		return result;
        	}else{
        		
        		result = list2;
        		next = list2.next;
        		result.next = Merge(list1,next);
        		return result;
        	}
        }
        return null;
    }
```
