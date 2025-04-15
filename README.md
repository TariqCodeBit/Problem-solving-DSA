#  <img src="https://cdn.iconscout.com/icon/free/png-256/free-leetcode-3521542-2944960.png" alt="LeetCode Icon" width="24" height="24"> LeetCode Solutions

## Table of Contents
- [Problem 1: Palindrome Number ](#problem-1-palindrome-number)
- [Problem 2: Reverse Integer](#problem-2-reverse-integer)
- [Problem 3: Roman to Integer](#problem-3-roman-to-integer)
- [Problem 4: Rotate Image](#problem-4-rotate-image)
- [Problem 5:  Number of 1 Bits](#problem-5--number-of-1-bits)
- [Problem 6: Reverse String](#problem-6-reverse-string)
- [Problem 7: Two Sum](#problem-7-two-sum)




- [Problem 11:  Two Sum II -sorted](#problem-11--two-sum-ii--sorted)
- [Problem 12:  Best Time to Buy & sell stock](#problem-12--best-time-to-buy--sell-stock)
- [Problem 13:  Valid Anagram](#problem-13--valid-anagram)
- [Problem 14: Fizz Buzz](#problem-14-fizz-buzz)
- [Problem 15: Merge String Alternately](#problem-15-merge-string-alternately)




















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
- **input --> "III" -->  output --> 3**
 - **input --> "MCMXCIV" -->  output --> 1994**

---
## Core Mathematical Idea

---
## Solution steps
  

---
## Note
 - **The Time Complexity is **O(n)****
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
## Problem 4: Rotate Image

- **Name**: ***48.  Rotate Image***
- **Link**: [Problem Link](https://leetcode.com/problems/rotate-image/description/)
- **Category**: ****Math / Matrix / Array****
- **Level**:  *****Medium*****

---

## Brief Description
- ***rotate the image by 90 degrees***
- **Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]**
- **Output: [[7,4,1],[8,5,2],[9,6,3]]**
---
## Core Mathematical Idea

---
## Solution steps
   - ***First, swap the values diagonally, then swap the first value of each row with the last value of the same row.***

---
## Note
 - **The Time Complexity is **O(n^2)****
 - **The Space Complexity is O(1)**

---

## Code in [ C++]

### Code



```cpp
class Solution {
public:


         void Swapp(int& V1, int& V2) {
            if (&V1 == &V2) return; //if same Address return 
            V1 = V1 ^ V2;
            V2 = V1 ^ V2;
            V1 = V1 ^ V2;
         }
        
 void rotate(vector<vector<int>>& matrix) {
     int row = matrix.size();
     for (int i = 0; i < row; i++) {
         for (int j = 0; j <= i; j++) {
             Swapp(matrix[i][j], matrix[j][i]);//swap diagonally

         }
     }
     for (int i = 0; i < row; i++) {
         reverse(matrix[i].begin(), matrix[i].end());
         //swap the first value of each row with the last value of the same row.
     }
    }
};



```
---
## Problem 5:  Number of 1 Bits

- **Name**: ***191.   Number of 1 Bits***
- **Link**: [Problem Link](https://leetcode.com/problems/number-of-1-bits/description/)
- **Category**: ****Divide and Conquer / Bit Manipulation****
- **Level**:  *****Easy*****

---

## Brief Description
- **write a function that returns the number of set bits [1] in its binary**
- **Input: n = 11**
    - **Output: 3**
- **Input: n =128**
    - **Output: 1**

## Core Mathematical Idea
- **- Num % 2 = last Bit (if Number EVEN  last bit = 0 OR Number ODD last bit =1)**
- **Num  / 2 = Delete last bit**

---
## Solution steps
   
 - **using Num & 1 = last Bit   {return 0 or 1}** 
 - **using Num >> 1 = Delete last Bit [shift right]**


---
## Note
 - **The Time Complexity is **O(log(n))****
 - **The Space Complexity is O(1)**

---

## Code in [ C++]

### Code



```cpp
class Solution {
public:
    int hammingWeight(int n) {
        int countt=0;
        while(n !=0){
            if (n & 1){ //return last Bit
                countt++;
            }
            n=n >> 1;// Delet last Bit
        }
        return countt;
        
    }
};

```
---
## Problem 6: Reverse String

- **Name**: ***344. Reverse String***
- **Link**: [Problem Link](https://leetcode.com/problems/reverse-string/description/)
- **Category**: ****Two Pointers / String****
- **Level**:  *****Easy*****

---

## Brief Description
- **Write a function that reverses a string. The input string is given as an array of characters s.**
 - **Input: s = ["h","e","l","l","o"]**
    - **Output: ["o","l","l","e","h"]**
 - **Input: s = ["H","a","n","n","a","h"]**
    - **Output: ["h","a","n","n","a","H"]**
 
## Core Mathematical Idea

---
## Solution steps
   
 

---
## Note


## Code in [ C++]

### Code



```cpp
class Solution { // sloution one
public:
//The Time Complexity is O(n)
//The Space Complexity is O(n)
    
    void reverseString(vector<char>& s) {
      vector<char> m = s;
      int n=m.size()-1;
            for (int i = n; i >=0; i--){
                s[n-i] = m[i];

          }
    }
};
//-----------------

class Solution{ // sloution Two best
public:
//The Time Complexity is O(n)
//The Space Complexity is O(1)
void reverseString(vector<char>&s){
   int left=0;
   int right=s.size()-1;
while(left<right){

    swap(s[left],s[right]);

    left++;
    right--;

        }
    }
};

```
## Problem 7: Two Sum

- **Name**: ***1. Two Sum***
- **Link**: [Problem Link](https://leetcode.com/problems/two-sum/description/)
- **Category**: ****Array / Hash Table****
- **Level**:  *****Easy*****

---

## Brief Description
- **Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.**

- **Input: nums = [2,7,11,15], target = 9**
    - **Output: [0,1]**
- **Input: nums = [3,2,4], target = 6**
    - **Output: [1,2]**

 
## Core Mathematical Idea

---
## Solution steps
   
 

---
## Note


## Code in [ C++]

### Code



```cpp
class Solution {// sloution one
public:
//The Time Complexity is O(n²)
//The Space Complexity is O(1)

    vector<int> twoSum(vector<int>& nums, int target) {
     
        int len=nums.size();
        for(int i =0;i < len ; i++){
        for(int j = i +1;j <len;j++){
            if(nums[i]+nums[j]==target)
             return {i,j};
            
            
        }
        }
        return {};
        
    }
};
//-----------------



class Solution { //solution Two
public:
//The Time Complexity is O(n)
//The Space Complexity is O(n)

    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> numMap; // Maps number to its index
        for (int i = 0; i < nums.size(); i++) {
            int complement = target - nums[i];
            if (numMap.find(complement) != numMap.end()) {
                return {numMap[complement], i};
            }
            numMap[nums[i]] = i;
        }
        return {};
    }
}


```

























---
## Problem 11:  Two Sum II -sorted

- **Name**: ***167. Two Sum II - Input Array Is Sorted***
- **Link**: [Problem Link](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)
- **Category**: ****Array/Two Pointers/Binary Search****
- **Level**:  *****Medium*****

---

## Brief Description
- **return the indices of the tow numbers, index1 and index2, added = target**
- **Input: numbers = [2,7,11,15], target = 9**
    - **Output: [1,2]**
- **numbers = [2,3,4], target = 6**
    - **Output: [1,3]**

## Core Mathematical Idea


---
## Solution steps
   
- **If the sum is too large, move right left to try a smaller number.**
- **If the sum is too small, move left right to try a larger number.**
- **If the sum equals target, return the indices.**


---
## Note
 - **The Time Complexity is **O(n)****
 - **The Space Complexity is O(1)**

---

## Code in [ C++]

### Code



```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {

        int left=0;
        int right=numbers.size()-1;
        while(true){
            if(numbers[left]+numbers[right] > target ){
                right--;
            } 
             if(numbers[left]+numbers[right] < target ){
             left++;
            }
            if(numbers[left]+numbers[right] == target){
                return {left+1 , right+1};
            }
        }
    return {};

    }
};

```
---
 ## Problem 12:  Best Time to Buy & sell stock

- **Name**: ***121. Best Time to Buy and Sell Stock***
- **Link**: [Problem Link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)
- **Category**: ****Array / Dynamic Programming****
- **Level**:  *****Easy*****

---

## Brief Description
- **You need to buy the stock on one day and sell it on a later day to make the highest possible profit. Profit is the difference between the selling price and the buying price (sell price - buy price).**

## Core Mathematical Idea


---
## Solution steps
   


---
## Note
 - **The Time Complexity is **O(n)****
 - **The Space Complexity is O(1)**

---

## Code in [ C++]

### Code



```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
       int Buy=prices[0];
       int profit=0;
        for(int i =0;i < prices.size();i++){
           if(Buy > prices[i])
            Buy=prices[i];
            else if(prices[i] - Buy > profit)
                profit=prices[i]-Buy;
        }
        return profit;
    }
};

```
---
## Problem 13:  Valid Anagram
- **Name**: ***242. Valid Anagram***
- **Link**: [Problem Link](https://leetcode.com/problems/valid-anagram/description/)
- **Category**: ****Hash Table / String / Sorting****
- **Level**:  *****Easy*****

---

## Brief Description
 - **Given two strings s and t, return true if t is an anagram of s, and false otherwise.**
 - **Input: s = "anagram", t = "nagaram"**
      - **Output: true**
 - **Input: s = "rat", t = "car"**

    - **Output: false**
---
## Core Mathematical Idea

---
## Solution steps
 
---
## Note
 - **The Time Complexity is O(N log (N) )**
  - **The Space Complexity is O(1)**

---

## Code in [ C++]

### Code



```cpp
class Solution {
public:
    bool isAnagram(string s, string t) {
        sort(s.begin(), s.end());
        sort(t.begin(), t.end());
        if(s==t)
        return true;
        else 
        return false;
    }
};
```
-----
## Problem 14: Fizz Buzz
- **Name**: ***412. Fizz Buzz***
- **Link**: [Problem Link](https://leetcode.com/problems/fizz-buzz/description/)
- **Category**: ****Math / String / Simulation***
- **Level**:  *****Easy*****

---

## Brief Description
- **answer[i] == "FizzBuzz" if i is divisible by 3 and 5.**
- **answer[i] == "Fizz" if i is divisible by 3.**
- **answer[i] == "Buzz" if i is divisible by 5.**
- **answer[i] == i (as a string) if none of the above conditions are true.**
 

---
## Core Mathematical Idea

---
## Solution steps
 
---
## Note
 - **The Time Complexity is O (N)**
  - **The Space Complexity is O(N)**

---

## Code in [ C++]

### Code



```cpp
class Solution {
public:
    vector<string> fizzBuzz(int n) {
        vector<string> ans;
        for(int i =1;i <= n;i++){
            if( ! (i % 15))
            ans.push_back("FizzBuzz");

            else if ( ! (i % 3))
            ans.push_back("Fizz");
            
            else if ( ! (i % 5))
            ans.push_back("Buzz");

            else 
            ans.push_back(to_string(i));
        }
        return ans;
        
    }
};

```
-----
## Problem 15: Merge String Alternately
- **Name**: ***1768. Merge Strings Alternately***
- **Link**: [Problem Link](https://leetcode.com/problems/merge-strings-alternately/description/?envType=study-plan-v2&envId=leetcode-75)
- **Category**: ****Two Pointers / String***
- **Level**:  *****Easy*****

---

## Brief Description
- **Input: word1 = "ab", word2 = "pqrs"**
    - **Output: "apbqrs"**
- **Input: word1 = "abcd", word2 = "pq"**
    - **Output: "apbqcd"**


---
## Core Mathematical Idea

---
## Solution steps
 
---
## Note
 - **The Time Complexity is O (N)**
  - **The Space Complexity is O(N)**

---

## Code in [ C++]

### Code



```cpp
class Solution {
public:
    string mergeAlternately(string word1, string word2) {
        string merged;
        int left=0;
        

        while( left < word1.length() || left < word2.length()){
            if( left < word1.length() )
            {
                 merged+= word1[left] ;
            }
            if(left < word2.length()){
                merged+=word2[left];
            }
          left++;
        }
        return merged;
        
    }
};
```
---