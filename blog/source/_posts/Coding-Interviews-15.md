---
title: Coding Interviews 15 反转链表
date: 2019-06-06 12:50:31
tags:
- LinkedList
- Data Structure
categories: 
- Coding Interview
---
# 剑指offer 第十五题 反转链表

## 题目描述
输入一个链表，输出该链表中倒数第k个结点。

<!--more-->
## 思路
every time, we start with three node a b->c
1. a b->c
2. a<-b c
3. b c->d
...

## 代码
``` bash
    public ListNode ReverseList(ListNode head) {
    	//this is an operation between three node
    	ListNode p = head;
    	ListNode next =null;
    	ListNode pre = null;
    	
    	if(p != null){
	    	while(p.next!=null){
	    		//1. split between p and p.next
	    		next = p.next;
	    		p.next = null;
	    		//2. reverse 
	    		p.next = pre;
	    		//3. change position
	    		pre = p;
	    		p = next;
	    	}
	    	
	    	p.next = pre;
        	
    	}

    	return p;
    }
```
