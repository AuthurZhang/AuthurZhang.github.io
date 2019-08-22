---
title: Coding Interviews 31 整数中出现1的次数
date: 2019-07-01 13:51:23
tags:
- String
categories: 
- Coding Interview
---
# 剑指offer 第三十一题 整数中出现1的次数

## 题目描述
求出1~13的整数中1出现的次数,并算出100~1300的整数中1出现的次数？为此他特别数了一下1~13中包含1的数字有1、10、11、12、13因此共出现6次,但是对于后面问题他就没辙了。ACMer希望你们帮帮他,并把问题更加普遍化,可以很快的求出任意非负整数区间中1出现的次数（从1 到 n 中1出现的次数）

<!--more-->
## 思路
transform Integer to String and check for every byte.

## 代码
``` java
    public int NumberOf1Between1AndN_Solution(int n) {
        int count = 0;
        for(int i = 1; i <= n ; i++){
            count+= CountOneInString(Integer.toString(i));
        }
        return count;
    }
    
    public int CountOneInString(String str){
        int count = 0;
        for(int i = 0; i < str.length(); i++){
            if(str.charAt(i) == '1'){
                count++;   
            }
        }
        return count;
    }
```

