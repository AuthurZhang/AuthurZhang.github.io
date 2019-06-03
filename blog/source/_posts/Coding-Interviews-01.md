---
title: Coding Interviews 01 二维数组中的查找
date: 2019-06-03 17:19:37
tags:
---
# 剑指offer第一题 二维数组中的查找
<!--more-->
## 题目描述
在一个二维数组中（每个一维数组的长度相同），每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。
## 思路
二重循环遍历数组即可。
## 代码
``` bash
    public boolean Find(int target, int [][] array) {
        for(int i = 0; i < array.length; i++){
            for(int j = 0; j < array[i].length; j++){
                if(array[i][j] == target){
                    return true;
                }
            }
        }
        return false;
    }
```