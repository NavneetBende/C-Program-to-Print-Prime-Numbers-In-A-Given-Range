# C-Program-to-Print-Prime-Numbers-In-A-Given-Range

Prime Numbers in a Given Range in C
A number that is divisible only by itself and 1 (e.g. 2, 3, 5, 7, 11).

The C program reduces the number of iterations within the loop. It is made to identify or calculate the prime numbers within a given range of numbers inserted by the user.

Ex:- if the user enters a range as 40 – 50 

In that range 41, 43, 47, these three number are prime number.

c program of find prime numbers in given range
Methods Discussed in page
We have discussed the following methods

Basic checking prime by only checking first n/2 divisors
Checking prime by only checking first √n divisors
Checking prime by only checking first √n divisors, but also skipping even iterations.
Method 1
Take lower and upper bound values from the user
Run a loop in the iteration of (i) b/w these bounds.
For each, i check if its prime or not using function checkPrime(i)
If i is prime print it else move to next iteration
Method used to check prime
Here we use the usual method to check prime. We however check the divisibility only till num/2.

As the range(num/2 + 1, num) won't be divisible anyways. Example 36 won't be divisible by anything b/w 19-35
Code
Run
#include <stdio.h>

int checkPrime(int num)
{
    // 0, 1 and negative numbers are not prime
    if(num < 2){
        return 0;
    }
    else{   
    // no need to run loop till num-1 as for any number x the numbers in
    // the range(num/2 + 1, num) won't be divisible anyways. 
    // Example 36 wont be divisible by anything b/w 19-35
        int x = num/2;
        for(int i = 2; i < x; i++)
        {
            if(num % i == 0)
            {
                return 0;
            }
        }
    }
    // the number would be prime if we reach here
    return 1;
}

int main()
{
    int a=10, b=20;
  
    
    for(int i=a; i <= b; i++){
        if(checkPrime(i))
            printf("%d ",i);
    }
 
    return 0;
}
//Time Complexity: O(N^2)
//Space Complexity O(1)
Output
11 13 17 19 
Method 2
The outer logic remains the same. Only the method to check prime changes to make code more optimized. Has better time complexity of O(√N)

Take lower and upper bound values from the user
Run a loop in the iteration of (i) b/w these bounds.
For each, i check if its prime or not using function checkPrime(i)
If i is prime print it else move to next iteration
Method used to check prime
A number n is not a prime if it can be factored into two factors a & b:
n = a * b

Now a and b can't be both greater than the square root of n, since then the product a * b would be greater than sqrt(n) * sqrt(n) = n.

So in any factorization of n, at least one of the factors must be smaller than the square root of n, and if we can't find any factors less than or equal to the square root, n must be a prime.

So we only need to run loop till sqrt(n) and not n or n/2
Code
Run

#include  <stdio.h>
#include  <math.h>

int checkPrime(int num)
{
    // 0, 1 and negative numbers are not prime
    if(num < 2){
        return 0;
    }
    else{   
    // A number n is not a prime, if it can be factored into two factors a & b:
    // n = a * b

    /*Now a and b can't be both greater than the square root of n, since
    then the product a * b would be greater than sqrt(n) * sqrt(n) = n.
    So in any factorization of n, at least one of the factors must be
    smaller than the square root of n, and if we can't find any factors
    less than or equal to the square root, n must be a prime.
    */
        for(int i = 2; i < sqrt(num); i++)
        {
            if(num % i == 0)
            {
                return 0;
            }
        }
    }
    // the number would be prime if we reach here
    return 1;
}

int main()
{
    int a, b;
    a=10,b=20;
    
    
    
    for(int i=a; i <= b; i++){
        if(checkPrime(i))
            printf("%d ",i);
    }
 
    return 0;
}
//Time Complexity: O(N√N)
//Space Complexity O(1)

// This method is obviously  faster as has better time complexity
Output
Enter the lower and upper ranges: 
20 40
23 25 29 31 37
Related Pages
Leap year

Prime Number

Sum of Digits of a number

Reverse of a number

Palindrome number

Method 3
The outer logic remains the same. Only the method to check prime changes to make code more optimized. Has same time complexity of O(√N).

But makes around half lesser checks

Take lower and upper bound values from the user
Run a loop in the iteration of (i) b/w these bounds.
For each, i check if its prime or not using function checkPrime(i)
If i is prime print it else move to next iteration
Method used to check prime
This method uses the assumption that –

We can simply check all divisors between [2, √num]
2 is the only even prime number
We can skip all even iterations in the loop
Code
Run
#include <stdio.h>
#include <math.h>

int checkPrime(int n)
{
    // 0 and 1 are not prime numbers
    // negative numbers are not prime
    if (n <= 1)
        return 0;

    // special case as 2 is the only even number that is prime
    else if (n == 2)
        return 1;

    // Check if n is a multiple of 2 thus all these won't be prime
    else if (n % 2 == 0)
        return 0;

    // If not, then just check the odds
    for (int i = 3; i <= sqrt(n); i += 2)
    {
        if (n % i == 0)
            return 0;
    }
    
    return 1;
}

int main()
{
    int a, b;
    a=10,b=20;
   
    
    for(int i=a; i <= b; i++){
        if(checkPrime(i))
            printf("%d ",i);
    }
 
    return 0;
}
//Time Complexity: O(N√N)
//Space Complexity O(1)

// This method is obviously faster as makes around half lesser comparision due skipping even iterations in the loop
Output
Enter the lower and upper ranges: 
30 50
31 37 41 43 47
