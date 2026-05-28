# Ex.No:1(A) INTRODUCTION TO JAVA PROGRAMMING, DATA TYPES, VARIABLES AND OPERATORS

## QUESTION:
Lovely has mastered printing in Java, and now she wants to learn how arithmetic operators work. She’s curious about how Java can add, subtract, multiply, divide, and find remainders of two numbers.

Write a Java program that:

Accepts two integer numbers from the user.

Demonstrates all 5 arithmetic operations:

Addition (+)

Subtraction (-)

Multiplication (*)

Division (/)

Modulus (%)

Displays the result of each operation in a separate line with a clear message.


## AIM:
Aim:
To write a Java program that reads two integer numbers from the user and performs basic arithmetic operations such as addition, subtraction, multiplication, division, and modulus, and displays the results.


## ALGORITHM :
1. Start the program.
2. Create an object of the Scanner class to take input from the user.
3. Read the first integer input from the user and store it in variable num1.
4. Read the second integer input from the user and store it in variable num2.
5. Calculate the sum of num1 and num2, and display the result.
6. Calculate the difference (num1 - num2), and display the result.
7. Calculate the product of num1 and num2, and display the result.
8. Calculate the quotient of num1 divided by num2, and display the result.
9. Calculate the remainder of num1 divided by num2, and display the result.
10. Close the Scanner object.




## PROGRAM:
 ```
/*
Program to implement variables and Operators using Java
Developed by: Vamsi Krishna G
RegisterNumber: 212223220120
*/
```

## Sourcecode.java:
```
import java.util.Scanner;

public class ArithmeticOperations {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int num1 = sc.nextInt();
        int num2 = sc.nextInt();

        System.out.println("Sum = " + (num1 + num2));
        System.out.println("Difference = " + (num1 - num2));
        System.out.println("Product = " + (num1 * num2));
        System.out.println("Quotient = " + (num1 / num2));
        System.out.println("Remainder = " + (num1 % num2));

        sc.close();
    }
}
```




## OUTPUT:
<img width="1252" height="354" alt="image" src="https://github.com/user-attachments/assets/b42fd06e-6ade-4df2-a3a3-8d25a65b9d7e" />



## RESULT:
Therefore the program has been executed successfully.




# Ex.No:1(B) CONDITIONAL STATEMENT

## QUESTION:
A pirate ship has a code lock that only opens if:

1)The input code is even, and

2)If it is less than 100, say "Weak Code".

3)If it is between 100 and 999, say "Strong Code".

4)If the code is odd, deny access.

## AIM:
Aim:
To write a Java program that accepts a code number and determines the security level based on the given conditions:
- If the code is even and less than 100 → Display "Weak Code"
- If the code is even and between 100 and 999 → Display "Strong Code"
- Otherwise → Display "Access Denied"

## ALGORITHM :
1. Start the program.
2. Create a Scanner object to read input from the user.
3. Read an integer value from the user and store it in variable 'code'.
4. Check if 'code' is even (code % 2 == 0):
     a. If 'code' is less than 100:
          - Print "Weak Code".
     b. Else if 'code' is between 100 and 999 (inclusive):
          - Print "Strong Code".
     c. Else:
          - Print "Access Denied".
5. If 'code' is odd:
     - Print "Access Denied".
6. End the program.






## PROGRAM:
 ```
/*
Program to implement a conditional statement using Java
Developed by: Vamsi Krishna G
RegisterNumber: 212223220120
*/
```

## SOURCE CODE:
```
import java.util.Scanner;

public class PirateCodeLock {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int code = sc.nextInt();

        if (code % 2 == 0) {
            if (code < 100) {
                System.out.println("Weak Code");
            } else if (code >= 100 && code <= 999) {
                System.out.println("Strong Code");
            }
            else
            {
                System.out.println("Access Denied");
            }
        } else {
            System.out.println("Access Denied");
        }
    }
}

```


## OUTPUT:
<img width="1253" height="395" alt="image" src="https://github.com/user-attachments/assets/4a2d9365-69a5-452d-bc72-f619377d3b5a" />


## RESULT:
Therefore,the program has been executed successfully.






# Ex.No:1(C) LOOPING STATEMENT

## QUESTION:
Display Factors of a Number


## AIM:
To write a Java program that reads an integer from the user and displays all the factors of the given number.

## ALGORITHM :
1.Start the program and read an integer n from the user.

2.Loop from 1 to n and check if each number i divides n exactly (i.e., n % i == 0).

3.If yes, print i as a factor.

4.Continue the loop until all factors are printed.

5.End the program.



## PROGRAM:
 ```
/*
Program to implement a Looping Statement using Java
Developed by: Vamsi Krishna G
RegisterNumber: 212223220120
*/
```

## SOURCE CODE:
```
import java.util.Scanner;

public class Factors {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();

        System.out.print("Factors: ");
        for (int i = 1; i <= n; i++) {
            if (n % i == 0) { 
                System.out.print(i + " ");
            }
        }
    }
}
```



## OUTPUT:
<img width="783" height="324" alt="image" src="https://github.com/user-attachments/assets/aec35b44-acab-4431-893b-df99fc8c8cd4" />


## RESULT:
Therefore, the program successfully reads a number from the user and computes its factors.





# Ex.No:1(D) ARRAYS

## QUESTION:
Write a Java program to find the index of a given element in an array

## AIM:
To write a Java program that reads an array of integers and finds the index of a given element within the array.

## ALGORITHM :
1.Start the program and read the size of the array n.

2.Read n integer elements and store them in the array a[ ].

3.Read the element x whose index needs to be found.

4.Traverse the array from index 0 to n-1:

     If a[i] == x, print the index i and terminate the program.

5.If the loop finishes without a match, print "Element not found".

6.End the program.	





## PROGRAM:
 ```
/*
Program to implement a Array concept using Java
Developed by: Vamsi Krishna G
RegisterNumber: 212223220120
*/
```

## SOURCE CODE:
```
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int a[] = new int[n];
        for (int i = 0; i < n; i++) 
        {
        a[i] = sc.nextInt();
        }
        
        int x = sc.nextInt();
        for (int i = 0; i < n; i++) {
            if (a[i] == x) {
                System.out.println(i);
                return;
            }
            
        }
        System.out.println("Element not found");
        
    }
}
```




## OUTPUT:
<img width="558" height="590" alt="image" src="https://github.com/user-attachments/assets/0d53717f-affe-4aaf-b448-35ef728bee48" />



## RESULT:
Therefore the program successfully searches the array for the given element.





# Ex.No:1(E) STRINGS AND MATH FUNCTION

## QUESTION:
Write a Java program to find the absolute value of a number using Math.abs().

## AIM:
To write a Java program that finds the absolute value of a given number using the Math.abs() method.

## ALGORITHM :
1.Start the program and create a Scanner object.

2.Read a number n (can be integer or decimal) from the user.

3.Use the built-in function Math.abs(n) to compute its absolute value.

4.Display the calculated absolute value.

5.End the program.



## PROGRAM:
 ```
/*
Program to implement a Strings and Math Function using Java
Developed by: Vamsi Krishna G
RegisterNumber: 212223220120
*/
```


## SOURCE CODE:
```
import java.util.*;
public class demo
{
    public static void main(String[] args)
    {
        Scanner sc=new Scanner(System.in);
        double n=sc.nextDouble();
        System.out.println("Absolute value = "+Math.abs(n));
    }
}
```


## OUTPUT:
<img width="744" height="288" alt="image" src="https://github.com/user-attachments/assets/5fab9f43-7f0e-491d-bbad-5c3b7979703e" />



## RESULT:
Therefore the program successfully reads a number and calculates its absolute value.



