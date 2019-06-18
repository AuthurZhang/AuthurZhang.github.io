---
title: Coding Interviews 19 顺时针打印矩阵
date: 2019-06-06 21:50:56
tags:
categories: 
- Coding Interview
---
# 剑指offer 第十九题 顺时针打印矩阵

## 题目描述
输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字，例如，如果输入如下4 X 4矩阵： 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 则依次打印出数字1,2,3,4,8,12,16,15,14,13,9,5,6,7,11,10.

<!--more-->
## 思路
rotate the matrix with counter clockwise, and cut the first until end.

## 代码
``` bash
    /**
     * 顺时针打印矩阵
     * @param matrix
     * @return
     */
    public ArrayList<Integer> printMatrix(int [][] matrix) {
        ArrayList<Integer> list = new ArrayList<Integer>();
        while(matrix.length > 1){
            //add
            for(int i = 0; i < matrix[0].length; i++){
                list.add(matrix[0][i]);
            }
            //change
            matrix = CounterClockwise(CutFirstLine(matrix));
        }

        //add
        for(int i = 0; i < matrix[0].length; i++){
            list.add(matrix[0][i]);
        }

        return list;
    }

    public int[][] CutFirstLine(int[][] matrix){
        int[][] newMatrix = new int[matrix.length-1][matrix[0].length];
        for(int i = 0; i < newMatrix.length; i++){
            for(int j = 0; j < newMatrix.length; j++){
                newMatrix[i][j] = matrix[i+1][j];
            }

        }
        return newMatrix;
    }


    /**
     * 逆时针旋转矩阵
     * @param matrix
     */
    public int[][] CounterClockwise(int[][] matrix){

        int[][] newMatrix = new int[matrix[0].length][matrix.length];
            for(int i = 0; i < newMatrix.length; i++){
                for(int j = 0; j < newMatrix[0].length; j++){
                    newMatrix[i][j] = matrix[j][matrix[0].length-i-1];
                }
            }
        return newMatrix;
    }
```
