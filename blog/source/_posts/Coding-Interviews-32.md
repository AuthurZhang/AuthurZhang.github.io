---
title: Coding Interviews 32 把数组排成最小的数
date: 2019-07-01 14:55:23
tags:
- String
categories: 
- Coding Interview
---
# 剑指offer 第三十二题 把数组排成最小的数

## 题目描述
输入一个正整数数组，把数组里所有数字拼接起来排成一个数，打印能拼接出的所有数字中最小的一个。例如输入数组{3，32，321}，则打印出这三个数字能排成的最小数字为321323。

<!--more-->
## 思路
Put into a list, sort and print.
The most important thing is Collections.sort() function to sort the ArrayList, and we need to override the comparator function.

## 代码
``` java
    public String PrintMinNumber(int [] numbers) {
        // put into a list, sort and print
        List<String> list = new ArrayList<>();

        for (int i = 0; i < numbers.length; i++){
            list.add(String.valueOf(numbers[i]));

        }

        Collections.sort(list, new Comparator<String>() {
            @Override
            public int compare(String o1, String o2) {
                
                String str1 = o1 + o2;
                String str2 = o2 + o1;
                
                return str1.compareTo(str2);
            }
        });

        StringBuilder stb = new StringBuilder();

        Iterator ite = list.iterator();
        while (ite.hasNext()){
            stb.append((String) ite.next());
        }

        return stb.toString();

    }
```



