---
title: Coding Interviews 08 跳台阶
date: 2019-06-05 09:49:44
tags:
- Recursion
categories: 
- Coding Interview
---
# 剑指offer 第八题 跳台阶

## 题目描述
一只青蛙一次可以跳上1级台阶，也可以跳上2级。求该青蛙跳上一个n级的台阶总共有多少种跳法（先后次序不同算不同的结果）。

<!--more-->
## 思路
Just write down the result array and we find that the Array is (1),1,2,3,5,8,13,21...
It is a Fibonacci array! 
But it start from the second num, be careful for the index.


## 代码
``` bash
    public int JumpFloor(int target) {
        
        return Fibonacci(target+1);
    }
    
    public int Fibonacci(int n) {
        //if n = 1 or 2 return
        //else recursion
        if(n == 1 || n == 2){
            return 1;
        }else{
            return Fibonacci(n-1)+Fibonacci(n-2);
        }

    }
```
