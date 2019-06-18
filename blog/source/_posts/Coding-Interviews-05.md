---
title: Coding Interviews 05 用栈实现队列
date: 2019-06-04 16:03:53
tags:
- Stack
- Queue
- Data Structure
categories: 
- Coding Interview
---

# 剑指offer 第五题 用栈实现队列

## 题目描述
用两个栈来实现一个队列，完成队列的Push和Pop操作。 队列中的元素为int类型。

<!--more-->
## 思路
use two stack to realize a queue, which is equal to realize "first in first out".
We need to realize the funcion of push and pop:
step1: the push of queue: just push into stack 1.
step2: the pop of the queue: 
                            1.if there is element in stack 2, pop it.
                            2.if not, pop all element in stack2 and then pop.

## 代码
``` bash
    public class QueueWithTwoStack {
        
        Stack<Integer> stack1 = new Stack<Integer>();
        Stack<Integer> stack2 = new Stack<Integer>();
        
        public void push(int node) {
            stack1.push(node);
        }
        
        public int pop() {
            
            if(!stack2.isEmpty()){
                return stack2.pop();
            }else{
                //let stack1 go to stack2
                while(!stack1.isEmpty()){
                    stack2.push(stack1.pop());
                }
                return stack2.pop();
            }
            
        }
    }
```
