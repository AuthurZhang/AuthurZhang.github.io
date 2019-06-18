---
title: Coding Interviews 13 调整数组顺序
date: 2019-06-05 16:50:18
tags:
categories: 
- Coding Interview
---
# 剑指offer 第十三题 调整数组顺序

## 题目描述
输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有的奇数位于数组的前半部分，所有的偶数位于数组的后半部分，并保证奇数和奇数，偶数和偶数之间的相对位置不变。

<!--more-->
## 思路
New two array and merge the two array.
Tips: ArrayList.toArray() will be useful: public <T> T[] toArray(T[] a)

Another solution: like bubble sort.

## 代码
``` bash
    public void reOrderArray(int [] array) {
        ArrayList<Integer> oddArray = new ArrayList<Integer>();
        ArrayList<Integer> evenArray = new ArrayList<Integer>();
        for(int i = 0; i < array.length; i++){
            if(array[i] % 2 == 1){
                oddArray.add(array[i]);
            }else{
                evenArray.add(array[i]);
            }
        }
        oddArray.addAll(evenArray);

        //change arraylist into int[]
        Integer[] temp  = oddArray.toArray(new Integer[oddArray.size()]);

        for(int i = 0; i < array.length; i++){
            array[i] = temp[i];
        }

    }
```
