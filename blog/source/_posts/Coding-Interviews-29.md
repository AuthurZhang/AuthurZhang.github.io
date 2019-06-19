---
title: Coding Interviews 29 最小的k个数
date: 2019-06-08 20:51:48
tags:
categories: 
- Coding Interview
---
# 剑指offer 第二十九题 最小的k个数

## 题目描述
输入n个整数，找出其中最小的K个数。例如输入4,5,1,6,2,7,3,8这8个数字，则最小的4个数字是1,2,3,4,。

<!--more-->
## 思路


## 代码
``` bash
    /**
     * 输入n个整数，找出其中最小的K个数。
     * 例如输入4,5,1,6,2,7,3,8这8个数字，则最小的4个数字是1,2,3,4,。
     * 堆排序 构建最大的堆
     * @param input
     * @param k
     * @return
     */
    public ArrayList<Integer> GetLeastNumbers_Solution(int [] input, int k) {

        if(input.length<k || k<=0){
            return new ArrayList<>();
        }



        //create maxHeap
        PriorityQueue<Integer> maxHeap = new PriorityQueue<>(k, new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                return o2.compareTo(o1);
            }
        });

        //add into the maxheap
        for(int i = 0; i < input.length; i++){
            if(maxHeap.size()<k){
               maxHeap.add(input[i]);
            }else{
                if(input[i]<maxHeap.peek()){
                    maxHeap.poll();
                    maxHeap.add(input[i]);
                }
            }
        }

        //turn maxheap to arraylist
        ArrayList<Integer> result = new ArrayList<>();
        result.addAll(maxHeap);
        return result;
    }
```
