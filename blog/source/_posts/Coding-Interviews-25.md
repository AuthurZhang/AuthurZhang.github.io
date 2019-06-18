---
title: Coding Interviews 25 复杂链表的复制
date: 2019-06-08 12:51:29
tags:
- LinkedList
- Data Structure
categories: 
- Coding Interview
---
# 剑指offer 第二十五题 复杂链表的复制

## 题目描述
输入一个复杂链表（每个节点中有节点值，以及两个指针，一个指向下一个节点，另一个特殊指针指向任意一个节点），返回结果为复制后复杂链表的head。（注意，输出结果中请不要返回参数中的节点引用，否则判题程序会直接返回空）

<!--more-->
## 思路
It is like BFS, use queue.
Tips: DFS, use stack or recursion.

## 代码
``` bash
    class RandomListNode {
        int label;
        RandomListNode next = null;
        RandomListNode random = null;

        RandomListNode(int label) {
            this.label = label;
        }
    }

    public class CloneComplexList {

        /**
        * 链表的复制 1步走 1.复制 2.链接 3.拆分
        * @param pHead
        * @return
        */
        public RandomListNode Clone(RandomListNode pHead)
        {
            //step 1 copy
            RandomListNode p = pHead;
            while(p != null){
                RandomListNode pNext = new RandomListNode(p.label);
                pNext.next = p.next;
                p.next = pNext;
                p = pNext.next;
            }

            //step 2 link
            p = pHead;
            while (p != null){
                RandomListNode pNext = p.next;
                pNext.random = p.random.next;
                p = pNext.next;
            }

            //step3 split
            p = pHead;
            RandomListNode pClone = null;
            if(p!= null){
                pClone = p.next;
            }
            while (p!=null){
                RandomListNode pNext = p.next;
                if(pNext.next!=null){
                    p.next = pNext.next;
                    pNext.next = p.next.next;
                    p = p.next;

                }else{
                    p.next = null;
                }
            }

            return pClone;

        }
    }
```

