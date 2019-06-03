---
title: Coding Interviews 02 替换空格
date: 2019-06-03 17:38:38
tags:
---
# 剑指offer第二题 替换空格
## 题目描述
请实现一个函数，将一个字符串中的每个空格替换成“%20”。例如，当字符串为We Are Happy.则经过替换之后的字符串为We%20Are%20Happy。
## 思路
使用java中String类的`replaceAll()`函数即可。
## 代码
``` bash
    public String replaceSpace(StringBuffer str) {
        String a = str.toString();
        String result = a.replaceAll(" ", "%20");
        return result;
    }
```