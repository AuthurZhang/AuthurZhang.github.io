---
title: Coding Interviews 33 丑数
date: 2019-07-02 14:55:23
categories: 
- Coding Interview
---
# 剑指offer 第三十三题 丑数

## 题目描述
把只包含质因子2、3和5的数称作丑数（Ugly Number）。例如6、8都是丑数，但14不是，因为它包含质因子7。 习惯上我们把1当做是第一个丑数。求按从小到大的顺序的第N个丑数。

<!--more-->
## 思路
like the relationship function of DP
ug[i] = ug[before]*2 || ug [before*3] || ug[before]*5

## 代码
``` java
    public int GetUglyNumber_Solution(int index) {
        
        if(index == 0){
            return 0;
        }
        //like dp
        int[] uglyArray = new int[index];
        uglyArray[0] = 1;
        int para2 = 0;
        int para3 = 0;
        int para5 = 0;

        //ug[i] = ug[before]*2 || ug [before*3] || ug[before]*5
        for(int i = 1; i < index; i++){
            uglyArray[i] = Math.min(uglyArray[para2]*2,
                    Math.min(uglyArray[para3]*3,uglyArray[para5]*5));
            if(uglyArray[i] == uglyArray[para2]*2){
                para2++;
            }
            if(uglyArray[i] == uglyArray[para3]*3){
                para3++;
            }
            if(uglyArray[i] == uglyArray[para5]*5){
                para5++;
            }
        }

        return uglyArray[index-1];
    }
```

