---
title: Coding Interviews 21 栈的压入，弹出序列
date: 2019-06-07 14:51:09
tags:
- Stack
- Data Structure
categories: 
- Coding Interview
---
# 剑指offer 第二十一题 栈的压入，弹出序列

## 题目描述
输入两个整数序列，第一个序列表示栈的压入顺序，请判断第二个序列是否可能为该栈的弹出顺序。假设压入栈的所有数字均不相等。例如序列1,2,3,4,5是某栈的压入顺序，序列4,5,3,2,1是该压栈序列对应的一个弹出序列，但4,3,5,1,2就不可能是该压栈序列的弹出序列。（注意：这两个序列的长度是相等的）

<!--more-->
## 思路
Create an assitant stack and simulate the process.
Compare the peek of the stack to the number in the array (if the same, remove together).

## 代码
``` bash
    public boolean IsPopOrder(int [] pushA,int [] popA) {
        if(pushA.length == 0 || popA.length == 0 ){
            return false;
        }

        Stack<Integer> stack = new Stack<>();
        int indexOfpopA = 0;
        // if top equal to popA if is remove together
        //if not, push into the stack
        for(int i = 0; i < pushA.length; i++){
            // first push
            stack.push(pushA[i]);
            //compare and remove
            while (stack.peek() == popA[indexOfpopA]){
                stack.pop();
                indexOfpopA++;
                if(indexOfpopA >= popA.length){
                    return stack.isEmpty();
                }
            }
        }
        return stack.isEmpty();
    }

```
