---
title: Coding Interviews 12 数值的整次方
date: 2019-06-05 13:50:14
tags:
categories: 
- Coding Interview
---
# 剑指offer 第十二题 数值的整次方

## 题目描述
给定一个double类型的浮点数base和int类型的整数exponent。求base的exponent次方。

<!--more-->
## 思路
Use loop and consider the condition that exponent < 0.

## 代码
``` bash
    public double Power(double base, int exponent) {
		double result = 1;
		if(exponent >= 0){
			for(int i = 0; i < exponent; i++){
				result *= base;
			}
			
			return result;
		}else{
			for(int i = 0; i < -exponent; i++){
				result /=base;
			}
			return result;
		}
    }
```
