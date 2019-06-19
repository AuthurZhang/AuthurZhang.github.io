---
title: Coding Interviews 28 数组中超过一半的数字
date: 2019-06-08 15:51:43
tags:
- Tree
- Data Structure
categories: 
- Coding Interview
---
# 剑指offer 第二十八题 数组中超过一半的数字

## 题目描述
数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。例如输入一个长度为9的数组{1,2,3,2,2,2,5,4,2}。由于数字2在数组中出现了5次，超过数组长度的一半，因此输出2。如果不存在则输出0

<!--more-->
## 思路
Use hashmap to count and find the great num.

## 代码
``` bash
    /**
     * 数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。
     * @param array
     * @return
     */
    public int MoreThanHalfNum_Solution(int [] array) {
        int criterion = array.length/2;
        //HashMap for count
        HashMap<Integer,Integer> hashMap = new HashMap<>();
        for(int i = 0; i < array.length; i++){
            if(!hashMap.containsKey(array[i])){
                hashMap.put(array[i],1);
            }else{
                hashMap.put(array[i],hashMap.get(array[i])+1);
            }
        }

        //traversing
        int result = 0;
        for(Integer key : hashMap.keySet()){
            if(hashMap.get(key)>criterion){
                result =  key;
            }
        }

        return result;
    }
```
