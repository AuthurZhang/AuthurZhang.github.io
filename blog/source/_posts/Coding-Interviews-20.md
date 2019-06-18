---
title: Coding Interviews 20 包含min函数的栈
date: 2019-06-07 12:51:03
tags:
- Stack
- Data Structure
categories: 
- Coding Interview
---
# 剑指offer 第二十题 包含min函数的栈

## 题目描述
定义栈的数据结构，请在该类型中实现一个能够得到栈中所含最小元素的min函数（时间复杂度应为O（1））。

<!--more-->
## 思路
We need another data structure to sotre the min list.(Use stack may be the best way)

## 代码
``` bash
    public class MinStack {

        //方法二：建立辅助栈

        Stack<Integer> stack = new Stack<>();
        ArrayList<Integer> list = new ArrayList<>();

        /**
        * 定义栈的数据结构
        * 请在该类型中实现一个能够得到栈中所含最小元素的min函数（时间复杂度应为O（1））。
        * @param args
        */
        public static void main(String[] args) {

        }

        public void push(int node) {
            stack.push(node);


            if(!list.isEmpty()){
                int index = 0;
                while(index<list.size()){
                    if(node > list.get(index)){
                        list.add(index, node);
                        break;
                    }
                    index++;
                }

                if(index == list.size()){
                    list.add(node);
                }
            }else{
                list.add(node);
            }
        }

        public void pop() {
            Integer a = stack.pop();
            list.remove(a);
        }

        public int top() {
            return stack.peek();
        }

        public int min() {
            return list.get(list.size()-1);
        }
    }

```
