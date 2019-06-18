---
title: Coding Interviews 09 变态跳台阶
date: 2019-06-05 10:49:49
tags:
categories: 
- Coding Interview
---
# 剑指offer 第九题 变态跳台阶

## 题目描述
一只青蛙一次可以跳上1级台阶，也可以跳上2级……它也可以跳上n级。求该青蛙跳上一个n级的台阶总共有多少种跳法。

<!--more-->
## 思路
Just write down the result array and we find that the Array is 1,2,4,8...
It is a simple array(every time by 2).


## 代码
``` bash
    public int JumpFloorII(int target) {
        if(target == 0 || target == 1){
            return 1;
        }else{
            return 2*JumpFloorII(target-1);
        }
        // or 
        //return Math.pow(2,target-1);
    }
```
