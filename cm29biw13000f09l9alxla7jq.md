---
title: "Leetcode 13 — Roman to Integer"
seoTitle: "Leetcode 13: Roman Numerals to Integers"
seoDescription: "Efficiently convert Roman numerals to integers with algorithm examples and performance insights. Explore a solution for the LeetCode challenge"
datePublished: Mon Oct 14 2024 17:58:47 GMT+0000 (Coordinated Universal Time)
cuid: cm29biw13000f09l9alxla7jq
slug: leetcode-13-roman-to-integer
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1728928292343/9e48fe7a-8916-4bbc-b367-51da212fd195.jpeg
tags: java, dsa, leetcode, leetcode-solution, dsainjava, romantointeger

---

Question Link : [Roman to Integer](https://leetcode.com/problems/roman-to-integer)

### Problem Statement :

Roman numerals are represented by seven different symbols: `I`, `V`, `X`, `L`, `C`, `D` and `M`.

Symbol       Value  
I             1  
V             5  
X             10  
L             50  
C             100  
D             500  
M             1000

For example, `2` is written as `II` in Roman numeral, just two ones added together. `12` is written as `XII`, which is simply `X + II`. The number `27` is written as `XXVII`, which is `XX + V + II`.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not `IIII`. Instead, the number four is written as `IV`. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as `IX`. There are six instances where subtraction is used:

*   `I` can be placed before `V` (5) and `X` (10) to make 4 and 9.
*   `X` can be placed before `L` (50) and `C` (100) to make 40 and 90.
*   `C` can be placed before `D` (500) and `M` (1000) to make 400 and 900.

Given a roman numeral, convert it to an integer.

**Example 1:**

Input: s = "III"  
Output: 3  
Explanation: III = 3.

**Example 2:**

Input: s = "LVIII"  
Output: 58  
Explanation: L = 50, V= 5, III = 3.

**Example 3:**

Input: s = "MCMXCIV"  
Output: 1994  
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.

**Constraints:**

*   `1 <= s.length <= 15`
*   `s` contains only the characters `('I', 'V', 'X', 'L', 'C', 'D', 'M')`.
*   It is **guaranteed** that `s` is a valid roman numeral in the range `[1, 3999]`.

### **Solution:**

#### **Approach : Comparing the roman numbers with the next one**

Firstly, we will implement the switch statements to calculate and get the value of the roman numberals. Then we will take integer value of each roman numberal from the input string and compare it with the integer value of the next roman numeral. If the next roman numberal is greater than the previous one then we will substract it from the total sum otherwise we will add it to the sum.

### **Explanation :**

Before running the logic for the program, we used the `System.gc()` command to run the garbage collector in java and release the memory.

Now, we will define four variables as below :

1. `sum`= total sum of the integer values of each roman numeral

2. `num`= the current roman numeral value in the iteration.

3. `next`= the next roman numeral value after the current number.

4. `strLength`= the length of the roman number.

> **Note**: We are defining variable for the string length outside the for loop so that the program only checks the length 1 time for the string. If we check the string length inside the for loop codition then it will check the String length for every iteration.

Now, we will use for loop to iterate over each character(roman numeral) in the roman number string. We will define a switch which will check the current index character and will assign it’s integral value to `num` variable. Similarly, the 2nd switch is defined for getting the integral value of the next character from the roman number string and store it in the `next` variable. Before the 2nd switch statement, we check if the current value of the iteration index is not the same as `strLength— 1`as it will cause an **ArrayIndexOutOfBound** Exception for the last iteration when there will be no next numeral.

Now, after getting the values of both the current and next roman numerals, we will check if the current number is less than next. If it’s less than next number then it means that we need to subtract that numeral value from the next roman number value or the `sum` . Else we can directly add the current number value to the `sum` variable.

Finally, at the end of the program we will return the total sum.

### **Performance :**

![Performance](https://cdn.hashnode.com/res/hashnode/image/upload/v1728928290981/358887e1-b208-4522-b17c-bc81db99b6b7.png)

### **Code :**
```java
class Solution {  
  
    static {  
        System.gc();  
    }  
      
    public int romanToInt(String s) {  
  
        int sum=0;  
        int num=0;  
        int next=0;  
        int strLength=s.length();  
  
        for(int i=0; i<strLength;i++){  
  
            switch(s.charAt(i)){  
                case 'I' -> num = 1;  
                case 'V' -> num = 5;  
                case 'X' -> num = 10;  
                case 'L' -> num = 50;  
                case 'C' -> num = 100;  
                case 'D' -> num = 500;  
                case 'M' -> num = 1000;  
            }  
            if(i<strLength-1){  
                switch(s.charAt(i+1)){  
                    case 'I' -> next = 1;  
                    case 'V' -> next = 5;  
                    case 'X' -> next = 10;  
                    case 'L' -> next = 50;  
                    case 'C' -> next = 100;  
                    case 'D' -> next = 500;  
                    case 'M' -> next = 1000;  
                }  
            }  
  
            if(num < next) sum-=num;  
            else sum+=num;  
        }  
  
        return sum;  
    }  
}
```