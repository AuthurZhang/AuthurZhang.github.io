---
title: Coding Interviews 11 二进制中1的个数
date: 2019-06-05 12:50:04
tags:
- Bit Operation
categories: 
- Coding Interview
---
# 剑指offer 第十一题 二进制中1的个数

## 题目描述
输入一个整数，输出该数二进制表示中1的个数。其中负数用补码表示。

<!--more-->
## 思路
Use the bit operation.
In Java, int is 32 bit.
Use loop to calculate every position.

## 代码
``` bash
    public int NumberOf1(int n) {
        int count = 0;
        for(int i = 0; i < 32; i++){
            int temp = n & 0x00000001;
            if(temp == 1){
                count++;
            }
            n = n>>1;
        }
        return count;
    }  
```
