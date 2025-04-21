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
- [Problem 16: Search a 2D Matrix](#problem-16-search-a-2d-matrix)
- [Problem 17: Factorial Trailing Zeroes](#problem-17-factorial-trailing-zeroes)
- [Problem 18: Reverse Words in a String](#problem-18-reverse-words-in-a-string)
- [Problem 19: Valid Palindrome](#problem-19-valid-palindrome)
- [Problem 20: Excel Sheet Column Title](#problem-20-excel-sheet-column-title)
-[Problem 21: Calculate Score After Performing Instructions](#problem-21-calculate-score-after-performing-instructions)


















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
## Problem 16: Search a 2D Matrix
- **Name**: ***74. Search a 2D Matrix***
- **Link**: [Problem Link](https://leetcode.com/problems/search-a-2d-matrix/description/?envType=problem-list-v2&envId=matrix)
- **Category**: ****Array / Binary Search / Matrix****
- **Level**:  *****Medium*****

---

## Brief Description
- **Given an integer target, return true if target is in matrix or false otherwise.**
- **Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3**
   - **Output: true**
- **Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13**
   - **Output: false**

---
## Core Mathematical Idea

---
## Solution steps
 
---
## Note
 - **The Time Complexity is O(N∗M)**
  - **The Space Complexity is O(1)**

---

## Code in [ C++]

### Code



```cpp
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
          vector<vector<int>>::iterator ite;

  for (ite = matrix.begin(); ite != matrix.end(); ite++) {
      vector<int> ::iterator col;
      for (col = ite->begin(); col != ite->end(); col++) {

          if (*col == target)
              return true;
          
      }
   }
  return false;
    }
};
```
---
## Problem 17: Factorial Trailing Zeroes
- **Name**: ***172. Factorial Trailing Zeroes***
- **Link**: [Problem Link](https://leetcode.com/problems/factorial-trailing-zeroes/description/)
- **Category**: ****Math****
- **Level**:  *****Medium*****

---

## Brief Description
 - **Given an integer n, return the number of trailing zeroes in n!.**
  - **Example 1:**

     - **Input: n = 3**
       -  **Output: 0**
            - **Explanation: 3! = 6, no trailing zero.**
  - **Example 2:**

    - **Input: n = 5**
      - **Output: 1**
         - **Explanation: 5! = 120, one trailing zero.**


---
## Core Mathematical Idea
- **The number of trailing zeros in 𝑛!  equals the number of factors of  5 in the prime factorization of 𝑛! , because the factors of 5 are the limiting facto(bottleneck) compared to the factors of 2. The formula:**

---
## Solution steps
 
---
## Note
 - **The Time Complexity is O(log N)**
  - **The Space Complexity is O(1)**

---

## Code in [ C++]

### Code



```cpp
class Solution {
public:
    int trailingZeroes(int n) {
        if(n <= 0) return 0;

        int count = 0;
        for (short i = 5; i <= n; i *= 5) {
            count += n / i;
        }
        return count;
    }
};
```
---

## Problem 18: Reverse Words in a String
- **Name**: ***151. Reverse Words in a String***
- **Link**: [Problem Link](https://leetcode.com/problems/reverse-words-in-a-string/description/)
- **Category**: ****Two Pointers / String****
- **Level**:  *****Medium*****

---

## Brief Description
 - **Given an input string s, reverse the order of the words.**
 - **Input: s = "the sky is blue"**
    - **Output: "blue is sky the"**

---
## Core Mathematical Idea

---
## Solution steps
 
---
## Note
 - **The Time Complexity is O(N)**
  - **The Space Complexity is O(N)**

---

## Code in [ C++]

### Code



```cpp
class Solution {
public:
   vector<string>split(string s, string delemt = " ") {
	vector<string> revers;
	string word = "";
	int pos;
	while ((pos=s.find(delemt)) != std::string::npos) {

		word = s.substr(0, pos);
		if (word != "")
		{
			revers.push_back(word);
		}
		s.erase(0, pos + delemt.length());


	}if (s != "") {
		revers.push_back(s);
	}
	return revers;
}


string reverseWords(string s) {
	vector<string>Vstr = split(s);
	string Delim = " ";
	string rev = "";
	int right = Vstr.size() - 1;
	while (!Vstr.empty()) {
		rev += Vstr[right] + Delim;
		Vstr.pop_back();
		right--;
	}
	return rev.substr(0, rev.length() - Delim.length());
}
};
```
---
## Problem 19: Valid Palindrome
- **Name**: ***125. Valid Palindrome***
- **Link**: [Problem Link](https://leetcode.com/problems/valid-palindrome/description/?envType=study-plan-v2&envId=top-interview-150)
- **Category**: ****Two Pointers / String****
- **Level**:  *****Easy*****

---

## Brief Description
- **Given a string s, return true if it is a palindrome, or false otherwise.**
- **Input: s = "A man, a plan, a canal: Panama"**
  - **Output: true**
    - **Explanation: "amanaplanacanalpanama" is a palindrome.**

- **Input: s = "race a car"**
  - **Output: false**
    - **Explanation: "raceacar" is not a palindrome.**
---
## Core Mathematical Idea

---
## Solution steps
 
---
## Note
```cpp
isalnum (char) // if the character is alphabetic (a-z, A-Z) or numeric (0-9) return true else return false (!,@,#,$,^,,,.)
```
 - **The Time Complexity is O(N)**
  - **The Space Complexity is O(1)**

---

## Code in [ C++]

### Code



```cpp
class Solution {
public:
    bool isPalindrome(string s) {
        
        int left=0;
        int right=s.length()-1;
        while(left < right){

                    while(left < right && ! isalnum(s[left])){
                        left++;
                    }
                    while(left < right && ! isalnum(s[right])){
                        right--;
                    }
                    if(tolower(s[left]) != tolower(s[right]))
                    return false;

            right--;
            left++;
        }
        return true;
    }
};
```
---
## Problem 20: Excel Sheet Column Title
- **Name**: ***168. Excel Sheet Column Title***
- **Link**: [Problem Link](https://leetcode.com/problems/excel-sheet-column-title/description/)
- **Category**: ****Math / String****
- **Level**:  *****Easy*****

---

## Brief Description
 - **Given an integer columnNumber, return its corresponding column title as it appears in an Excel sheet.**
  - **Input: columnNumber = 1**
    - **Output: "A"**
  - **Input: columnNumber = 28**
    - **Output: "AB"**
---
## Core Mathematical Idea

---
## Solution steps
 
---
## Note

 - **The Time Complexity is O(log(N))**
  - **The Space Complexity is O(1)**

---

## Code in [ C++]

### Code



```cpp
class Solution {
public:
    string convertToTitle(int columnNumber) {
        
        string str="";
        int rev=0;
        while(columnNumber > 0){
            columnNumber--;
            rev=columnNumber % 26;
            str=char('A'+rev)+str;
            columnNumber/=26;
        }
        return str;
    }
};
```
---
## Problem 21: Calculate Score After Performing Instructions
- **Name**: ***3522. Calculate Score After Performing Instructions***
- **Link**: [Problem Link](https://leetcode.com/problems/calculate-score-after-performing-instructions/description/)
- **Category**: ****!****
- **Level**:  *****Medium*****

---

## Brief Description
- **You start at the first instruction at index i = 0 with an initial score of 0.**
- **If instructions[i] is "add":**
   - **Add values[i] to your score.**
   - **Move to the next instruction (i + 1).**
- **If instructions[i] is "jump":**
  - **Move to the instruction at index (i + values[i]) without modifying your score.
The process ends when you either:**

- **Go out of bounds (i.e., i < 0 or i >= n), or**
- **Attempt to revisit an instruction that has been previously executed. The revisited instruction is not executed.**
**Return your score at the end of the process.**


- **Input: instructions = ["jump","add","add","jump","add","jump"], values = [2,1,3,1,-2,-3]**

  - **Output: 1**
---
## Core Mathematical Idea

---
## Solution steps
 
---
## Note

 - **The Time Complexity is O(N)**
  - **The Space Complexity is O(N)**

---

## Code in [ C++]

### Code



```cpp
class Solution {
public:
    long long calculateScore(vector<string>& instructions, vector<int>& values) {
                long long score = 0;
        vector<bool> visited(values.size(), false); 
        vector<bool> added(values.size(), false);  
        int i = 0;

        while (i < values.size()) {
            if (i < 0 || i >= values.size()) {
                return -1;
            }
            if (visited[i]) { 
                return score; 
            }
            visited[i] = true; 

            if (instructions[i] == "jump") {
                i += values[i]; 
            }
            else { 
                if (!added[i]) { 
                    score += values[i];
                    added[i] = true;
                }
                i++; 
            }
        }
        return score;
    }
};

```
---
## Problem 22: Plus One
- **Name**: ***66. Plus One***
- **Link**: [Problem Link](https://leetcode.com/problems/plus-one/)
- **Category**: ****Array / Math****
- **Level**:  *****Easy*****

---

## Brief Description
- **Input: digits = [1,2,3]**
   - **Output: [1,2,4]**
     - **Explanation: The array represents the integer 123.**
     - **Incrementing by one gives 123 + 1 = 124.**
     - **Thus, the result should be [1,2,4].**

- **Input: digits = [9]**
   - **Output: [1,0]**
      - **Explanation: The array represents the integer 9.**
      - **Incrementing by one gives 9 + 1 = 10.**
      - **Thus, the result should be [1,0].**
 

---
## Core Mathematical Idea
```cpp
 int lenDigit= floor(log10(abs(Number)))+1; // return length the Number using Math
```
---
## Solution steps
 
---
## Note 


 - **The Time Complexity is O(N)**
  - **The Space Complexity is O(1)**

---

## Code in [ C++]

### Code



```cpp

class Solution {
public:
    vector<int> plusOne(vector<int>& digits) {
      
        for (int i = digits.size() - 1; i >= 0; i--) {
            // If the current digit is less than 9, increment it and return the result
            if (digits[i] < 9) {
                digits[i]++;
                return digits; // No carry needed, so we can return immediately
            }
            // If the digit is 9, set it to 0 and continue to propagate the carry
            else {
                digits[i] = 0;
            }
        }
        // If we exit the loop, all digits were 9, so add a 1 at the beginning
        digits.insert(digits.begin(), 1);
        return digits; 
    }
};

```
---