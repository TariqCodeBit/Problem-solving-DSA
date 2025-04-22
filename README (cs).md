#  <img src=https://static-00.iconduck.com/assets.00/c-sharp-c-icon-912x1024-j3yidw37.png alt="C# Icon" width="24" height="24">  Problem Solving 


-[problem 1 ](#problem-1-)






## problem 1 :
- **Write a program print the Multiplication Table From 1 to 10 as Follows:**
- **Output**
```output

                               Multiplication Table From 1 To 10

         1       2       3       4       5       6       7       8       9       10
_____________________________________________________________________________________
1 |     1       2       3       4       5       6       7       8       9       10
2 |     2       4       6       8       10      12      14      16      18      20
3 |     3       6       9       12      15      18      21      24      27      30
4 |     4       8       12      16      20      24      28      32      36      40
5 |     5       10      15      20      25      30      35      40      45      50
6 |     6       12      18      24      30      36      42      48      54      60
7 |     7       14      21      28      35      42      49      56      63      70
8 |     8       16      24      32      40      48      56      64      72      80
9 |     9       18      27      36      45      54      63      72      81      90
10|     10      20      30      40      50      60      70      80      90      100
```
```c#
using System;
namespace quick
{
    internal class Program
    {
        static void PrintTableHeader()
        {
            Console.WriteLine("\t \t \t Multiplication Table From 1 To 10 ");
            for(int i =1;i <= 10; i++)
            {
                Console.Write($"\t {i}");
            }
            Console.WriteLine("\n_____________________________________________________________________________________________");
        }

        static void  ColumnSperator(int Num)
        {
            if(Num > 9)
                Console.Write($"{Num}|");
            
            else
                Console.Write("{0} |",Num);
            
        }
        static void PrintMultiplicationTable()
        {
            PrintTableHeader();
            for(int i = 1;i <= 10; i++)
            {    ColumnSperator(i);
                for(int j=1;j <= 10; j++)
                {
                    Console.Write($"\t{i * j}");
                }
                Console.WriteLine();
                
            }

        }
        static void Main(string[] args)
        {
            PrintMultiplicationTable();
            Console.ReadKey();
        }
    }
}
```
## problem 2 :