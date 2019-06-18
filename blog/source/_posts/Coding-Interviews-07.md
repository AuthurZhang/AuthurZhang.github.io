---
title: Coding Interviews 07 斐波那契数列
date: 2019-06-05 08:49:36
tags:
- Recursion
categories: 
- Coding Interview
---
# 剑指offer 第七题 斐波那契数列

## 题目描述
大家都知道斐波那契数列，现在要求输入一个整数n，请你输出斐波那契数列的第n项（从0开始，第0项为0）。

<!--more-->
## 思路
use recrusion. The Array is 1,1,2,3,5,8,13,21...
Tips: Fibonacci(0)  = 0 

## 代码
``` bash
    public static int Fibonacci(int n) {
        
        if(n==0){
            return 0;
        }

        //if n = 1 or 2 return
        //else recursion
        if(n == 1 || n == 2){
            return 1;
        }else{
            return Fibonacci(n-1)+Fibonacci(n-2);
        }

    }
```
