---
title: Coding Interviews 10 矩形覆盖
date: 2019-06-05 11:49:56
tags:
- Recursion
categories: 
- Coding Interview
---
# 剑指offer 第十题 矩形覆盖

## 题目描述
我们可以用2*1的小矩形横着或者竖着去覆盖更大的矩形。请问用n个2*1的小矩形无重叠地覆盖一个2*n的大矩形，总共有多少种方法？

<!--more-->
## 思路
Just write down the result array and we find that the Array is (1),1,2,3,5,8,13,21...
It is a Fibonacci array! 
Be careful for the index.


## 代码
``` bash
    public int RectCover(int target) {
        
        if(target == 0){
            return 0;
        }
        return Fibonacci(target+1);
    }
    
    public static int Fibonacci(int n) {
        //if n = 1 or 2 return
        //else recursion
        if(n == 1 || n == 2){
            return 1;
        }else{
            return Fibonacci(n-1)+Fibonacci(n-2);
        }

    }    
```


