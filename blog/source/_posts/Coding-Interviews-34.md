---
title: Coding Interviews 34 第一个只出现一次的字符
date: 2019-07-02 14:55:23
categories: 
- Coding Interview

---

# 剑指offer 第三十三题 第一个只出现一次的字符

## 题目描述

在一个字符串(0<=字符串长度<=10000，全部由字母组成)中找到第一个只出现一次的字符,并返回它的位置, 如果没有则返回 -1（需要区分大小写）

<!--more-->

## 思路

It will be easy to solve it with hashmap.

## 代码

```java
    public int FirstNotRepeatingChar(String str) {

        Map<Character,Integer> map = new LinkedHashMap<>();
        for(int i = 0; i < str.length(); i++){
            char character = str.charAt(i);
            if(!map.containsKey(character)){
                map.put(character,i);
            }else{
                map.put(character,-1);
            }
        }
        int result = -1;
        for( Character key : map.keySet()){
            if(map.get(key) != -1){
                result = map.get(key);
                return result;
            }
        }
        return result;
    }
```


