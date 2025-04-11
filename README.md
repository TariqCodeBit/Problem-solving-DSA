#  <img src="https://cdn.iconscout.com/icon/free/png-256/free-leetcode-3521542-2944960.png" alt="LeetCode Icon" width="24" height="24"> LeetCode Solutions

## Table of Contents
- [Problem 1: Palindrome Number ](#problem-1-palindrome-number)
- [Problem 2: Reverse Integer](#problem-2-reverse-integer)
- [Problem 3: Roman to Integer](#problem-3-roman-to-integer)





















## Problem 1: Palindrome Number
- **Name**: ***9. Palindrome Number***
- **Link**: [Problem Link](https://leetcode.com/problems/palindrome-number/description/)
- **Category**: ****Math****
- **Level**:  *****Easy*****

---

## Brief Description
 - **same when its digits are read from left to right or right to left.**
 - **121 --> 121 {true};**
 - **123 --> 321 {false};**

---
## Core Mathematical Idea
- **revers = revers * 10 + Num(last digit); // reversed**
---
## Solution steps
 - **using mod (%) 10 return last digit;**
     - **input --> -157 % 10 --> output--> -7;   output=(same sign Number[-157])**
 - **using (/) 10 Delete last digit;**
     - **input --> -157 / 10 --> output--> -15;** 

---
## Note
 - **The Time Complexity is O(log (x) )**
  - **The Space Complexity is O(1)**

---

## Code in [ C++]

### Code



```cpp
class Solution {
public:
  int Revers(int number){
        int Num=0;
        long int revers;
        while(number > 0){
            Num=number%10;
            number/=10;
         revers=revers*10+Num;

         }
   return revers;
}

        bool isPalindrome(int x) {
        if (x == Revers(x)) 
            return true;
    
        return false;
    }
};

```
-----
## Problem 2: Reverse Integer

- **Name**: ***7. Reverse Integer***
- **Link**: [Problem Link](https://leetcode.com/problems/reverse-integer/description/)
- **Category**: ****Math****
- **Level**:  *****Medium*****

---

## Brief Description
 - **Reversed.**
   - **121 --> 121**
   - **123 --> 321**

---
## Core Mathematical Idea
- **rev = rev * 10 + Num(last digit); // reversed**
---
## Solution steps
  - **using mod (%) 10 return last digit;**
     - **input --> -157 % 10 --> output--> -7; output=  (same sign Number[-157])**
 - **using (/) 10 Delete last digit;**
     - **input --> -157 / 10 --> output--> -15;** 


---
## Note
 - **The Time Complexity is **O(log (x))****
 - **The Space Complexity is O(1)**

---

## Code in [ C++]

### Code



```cpp
class Solution {
public:
    int reverse(int x) {
        int reversed = 0;
      int num=0;
        while (x != 0) {
           num  = x % 10;
            // Check for overflow before updating reversed
            // If reversed is greater than INT_MAX/10 or less than INT_MIN/10,
            // adding another digit would exceed 32-bit integer limits
            if ((reversed > INT_MAX / 10) || (reversed < INT_MIN / 10)) 
             return 0;  
             
                x = x / 10;
            reversed = reversed * 10 + num;
           
        }
        return reversed;
    }
};


```
-----
## Problem 3: Roman to Integer

- **Name**: ***13. Roman to Integer***
- **Link**: [Problem Link](https://leetcode.com/problems/roman-to-integer/description/)
- **Category**: ****Math / String / Hash Table****
- **Level**:  *****Easy*****

---

## Brief Description
 

---
## Core Mathematical Idea

---
## Solution steps
  

---
## Note
 - **The Time Complexity is **O(log (x))****
 - **The Space Complexity is O(1)**

---

## Code in [ C++]

### Code



```cpp

class Solution {
public:
      int romanToInt(string s) {
       int Num = 0;
     
       map<char, int> Roman;
       Roman['I'] = 1;
       Roman['V'] = 5;
       Roman['X'] = 10;
       Roman['L'] = 50;
       Roman['C'] = 100;
       Roman['D'] = 500;
       Roman['M'] = 1000;

       for (int i = s.length()-1; i >=0; i--) {
           
          
           if (i >0 && Roman[s[i-1]] < Roman[s[i ]]) {
               Num += (Roman[s[i ]] - Roman[s[i-1]]);
               i--;
           }else
           Num += Roman[s[i]];
           
       }
       return Num;
   }
    
};


```
---
    
