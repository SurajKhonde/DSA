---
description: how handle Mat
---

# Math

Count Digits

Given a number N, the task is to return the count of digits in this number.

### **Simple Iterative Solution to count digits in an integer**

The integer entered by the user is stored in the variable n. Then the while loop is iterated until the test expression n != 0 is evaluated to 0 (false).   We will consider 3456 as the input integer. &#x20;

1. After the first iteration, the value of n will be updated to 345 and the count is incremented to 1.
2. After the second iteration, the value of n will be updated to 34 and the count is incremented to 2.
3. After the third iteration, the value of n will be updated to 3 and the count is incremented to 3.
4. In the fourth iteration, the value of n will be updated to zero and the count will be incremented to 4. &#x20;
5. Then the test expression is evaluated ( n!=0 ) as false and the loop terminates with final count as 4.

Below is the implementation of the above approach:

```javascript
function countDigit(n) {
  if (n === 0) return 1;
  let count = 0;
  while (n !== 0) {
    n = Math.floor(n / 10);
    count++;
  }
  return count;
}

const n = 345289467;
console.log(`Number of digits: ${countDigit(n)}`);
```

**Time Complexity :** O(log10(n)) or θ(num digits)\
**Auxiliary Space:** O(1) or constant\


<mark style="color:red;">**Palindrome Numbers**</mark>

Given an integer, write a function that returns true if the given number is palindrome, else false. For example, 12321 is palindrome, but 1451 is not palindrome.

A simple approach to check if a number is Palindrome or not . This approach can be used when the number of digits in the given number is less than 10^18 because if the number of digits of that number exceeds 10^18, we can’t take that number as an integer since the range of long long int doesn’t satisfy the given number.

To check whether the given number is palindrome or not we will just reverse the digits of the given number and check if the reverse of that number is equal to the original number or not . If reverse of number is equal to that number than the number will be Palindrome else it will not a Palindrome.

```javascript
function checkPalindrome(n) {
  let reverse = 0;
  let temp = n;
  while (temp !== 0) {
    reverse = (reverse * 10) + (temp % 10);
    temp = Math.floor(temp / 10);
  }
  return reverse === n;
}

const n = 7007;
if (checkPalindrome(n)) {
  console.log("Yes");
} else {
  console.log("No");
}
```

**Time Complexity :** O(log(n)) or O(Number of digits in a given number)

**Auxiliary space** : O(1) or constant

<mark style="color:red;">**Factorial of a Number**</mark>

### What is the factorial of a number?

* Factorial of a non-negative integer is the multiplication of all positive integers smaller than or equal to n. For example factorial of 6 is 6\*5\*4\*3\*2\*1 which is 720.&#x20;
* A factorial is represented by a number and a  ” ! ”  mark at the end. It is widely used in permutations and combinations to calculate the total possible outcomes. A French mathematician Christian Kramp firstly used the exclamation.

Let’s create a factorial program using recursive functions. Until the value is not equal to zero, the recursive function will call itself. Factorial can be calculated using the following recursive formula.&#x20;

> _n! = n \* (n – 1)!_\
> _n == 1 if n = 0 or n = 1_

Below is the implementation:&#x20;

```javascript
function factorial(n) {
  if (n === 0 || n === 1) return 1;
  return n * factorial(n - 1);
}

const num = 5;
console.log(`Factorial of ${num} is ${factorial(num)}`);
```

**Time Complexity:** O(n)\
**Auxiliary Space:** O(n)

### **Iterative Solution to find factorial of a number:**

Factorial can also be calculated iteratively as recursion can be costly for large numbers. Here we have shown the iterative approach using both for and while loops.&#x20;

**Approach 1:** Using For loop&#x20;

Follow the steps to solve the problem:

* Using a for loop, we will write a program for finding the factorial of a number.&#x20;
* An integer variable with a value of 1 will be used in the program.&#x20;
* With each iteration, the value will increase by 1 until it equals the value entered by the user.&#x20;
* The factorial of the number entered by the user will be the final value in the fact variable.

Below is the implementation for the above approach:

```javascript
function factorial(n) {
  let res = 1;
  for (let i = 2; i <= n; i++) res *= i;
  return res;
}

const num = 5;
console.log(`Factorial of ${num} is ${factorial(num)}`);
```

**Time Complexity:** O(n)\
**Auxiliary Space:** O(<mark style="color:red;">1)</mark>

<mark style="color:red;">**Trailing Zeros in Factorial**</mark>

Given an integer n, write a function that returns count of trailing zeroes in n!. \
**Examples :**&#x20;

<pre><code><strong>Input: n = 5
</strong><strong>Output: 1 
</strong>Factorial of 5 is 120 which has one trailing 0.

<strong>Input: n = 20
</strong><strong>Output: 4
</strong>Factorial of 20 is 2432902008176640000 which has
4 trailing zeroes.

<strong>Input: n = 100
</strong><strong>Output: 24
</strong></code></pre>

1. **Approach:**\
   A simple method is to first calculate factorial of n, then count trailing 0s in the result (We can count trailing 0s by repeatedly dividing the factorial by 10 till the remainder is 0).\
   &#x20;
2. The above method can cause overflow for slightly bigger numbers as the factorial of a number is a big number (See factorial of 20 given in above examples). The idea is to consider prime factors of a factorial n. A trailing zero is always produced by prime factors 2 and 5. If we can count the number of 5s and 2s, our task is done. Consider the following examples.\
   **n = 5:** There is one 5 and 3 2s in prime factors of 5! (2 \* 2 \* 2 \* 3 \* 5). So a count of trailing 0s is 1.\
   **n = 11:** There are two 5s and eight 2s in prime factors of 11! (2 8 \* 34 \* 52 \* 7). So the count of trailing 0s is 2.\
   &#x20;
3. We can easily observe that the number of 2s in prime factors is always more than or equal to the number of 5s. So if we count 5s in prime factors, we are done. _How to count_ the _total number of 5s in prime factors of n!?_ A simple way is to calculate floor(n/5). For example, 7! has one 5, 10! has two 5s. It is not done yet, there is one more thing to consider. Numbers like 25, 125, etc have more than one 5. For example, if we consider 28! we get one extra 5 and the number of 0s becomes 6. Handling this is simple, first, divide n by 5 and remove all single 5s, then divide by 25 to remove extra 5s, and so on. Following is the summarized formula for counting trailing 0s.

```
Trailing 0s in n! = Count of 5s in prime factors of n!
                  = floor(n/5) + floor(n/25) + floor(n/125) + ....
```

Javascript

```javascript
function findTrailingZeros(n) {
  if (n < 0) return -1;

  let count = 0;

  for (let i = 5; n / i >= 1; i *= 5) {
    count += Math.floor(n / i);
  }

  return count;
}

const n = 100;
console.log(`Count of trailing 0s in ${n}! is ${findTrailingZeros(n)}`);
```

&#x20;

**Output :**&#x20;

```
Count of trailing 0s in 100! is 24 
```

_**Time Complexity:** O(log5n)_

_**Auxiliary Space:** O(1)_

<mark style="color:red;">**GCD or HCF of two Numbers**</mark>

GCD (Greatest Common Divisor) or HCF (Highest Common Factor) of two numbers is the largest number that divides both of them.&#x20;

For example, GCD of 20 and 28 is 4 and GCD of 98 and 56 is 14.&#x20;

A simple and old  approach is the **Euclidean algorithm by subtraction**

&#x20;It is a process of repeat subtraction, carrying the result forward each time until the result is equal to any one number being subtracted. If the answer is greater than 1, there is a GCD (besides 1). If the answer is 1, there is no common divisor (besides 1), and so both numbers are coprime

pseudo code for the above approach:

> _def gcd(a, b):_\
> &#x20; _if a == b:_\
> &#x20;   _return a_\
> &#x20; _if a > b:_\
> &#x20;   _gcd(a – b, b)_\
> &#x20; _else:_\
> &#x20;   _gcd(a, b – a)_

At some point, one number becomes factor of the other so instead of repeatedly subtracting till both become equal, we check if it is factor of the other. &#x20;

**For Example**  suppose a=98 & b=56  a>b so put a= a-b and b remains same. So  a=98-56=42  & b= 56 . Since b>a, we check if b%a==0. since answer is no we proceed further. Now b>a  so  b=b-a and a remain same. So b= 56-42 = 14 & a= 42   . Since a>b, we check if a%b==0 . Now the answer is yes. So we print smaller among a and b as H.C.F . i.e. 42 is  3 times of 14  so **HCF** is 14.&#x20;

likewise  when a=36  & b=60  ,here b>a  so b = 24 & a= 36 but a%b!=0.  Now a>b so a= 12 & b= 24  . and b%a==0. smaller among a and b is 12  which becomes  HCF of 36 and 60.  &#x20;

The idea is, GCD of two numbers doesn’t change if a smaller number is subtracted from a bigger number.&#x20;

Javascript

```javascript
// JavaScript program to find GCD of two numbers

// Recursive function to return gcd of a and b
function gcd(a, b) {
  // Everything divides 0
  if (a === 0) return b;
  if (b === 0) return a;

  // base case
  if (a === b) return a;

  // a is greater
  if (a > b) return gcd(a - b, b);
  return gcd(a, b - a);
}

// Driver program to test above function
const a = 98, b = 56;
console.log(`GCD of ${a} and ${b} is ${gcd(a, b)}`);
```

&#x20;

**Output**

```
GCD of 98 and 56 is 14
```

**Time Complexity:** O(min(a,b))\
**Auxiliary Space:** O(min(a,b))

Instead of Euclidean algorithm by subtraction, a better approach is present. We don’t perform subtraction here. we continuously divide the bigger number by the smaller number. More can be learned about this **efficient solution** by using modulo operator in [Euclidean algorithm](https://www.geeksforgeeks.org/euclidean-algorithms-basic-and-extended/).

Javascript

```javascript
const gcd = (a, b) => {
  return b === 0 ? a : gcd(b, a % b);
};

const a = 98, b = 56;
console.log(`GCD of ${a} and ${b} is ${gcd(a, b)}`);
```

&#x20;

**Output**

```
GCD of 98 and 56 is 14
```

**Time Complexity:** O(log(min(a,b))|\
**Auxiliary Space:** O(log(min(a,b))

The time complexity for the above algorithm is O(log(min(a,b))) the derivation for this is obtained from the analysis of the worst-case scenario. What we do is we ask what are the 2 least numbers that take 1 step, those would be (1,1). If we want to increase the number of steps to 2 while keeping the numbers as low as possible as we can take the numbers to be (1,2). Similarly, for 3 steps, the numbers would be (2,3), 4 would be (3,5), 5 would be (5,8). So we can notice a pattern here, for the nth step the numbers would be (fib(n), fib(n+1)).  So the worst-case time complexity would be O(n) where a>= fib(n) and b>= fib(n+1).&#x20;

Now Fibonacci series is an exponentially growing series where the ratio of nth/(n-1)th term approaches (sqrt(5)+1)/2 which is also called the golden ratio. So we can see that the time complexity of the algorithm increases linearly as the terms grow exponentially hence the time complexity would be log(min(a,b)).

<mark style="color:red;">**LCM of Two Numbers**</mark>\
LCM (Least Common Multiple) of two numbers is the smallest number which can be divided by both numbers.&#x20;

For example, LCM of 15 and 20 is 60, and LCM of 5 and 7 is 35.

A **simple solution** is to find all prime factors of both numbers, then find union of all factors present in both numbers. Finally, return the product of elements in union.

An **efficient solution** is based on the below formula for LCM of two numbers ‘a’ and ‘b’.&#x20;

```
 a x b = LCM(a, b) * GCD (a, b)

   LCM(a, b) = (a x b) / GCD(a, b)
```

We have discussed function to find GCD of two numbers. Using GCD, we can find LCM.&#x20;

Below is the implementation of the above idea:

```javascript

// Recursive function to return gcd of a and b
function gcd(a, b) {
  if (b === 0) return a;
  return gcd(b, a % b);
}

// Function to return LCM of two numbers
function lcm(a, b) {
  return (a / gcd(a, b)) * b;
}

// Driver program to test above function
const a = 15;
const b = 20;
console.log(`LCM of ${a} and ${b} is ${lcm(a, b)}`);
// Recursive function to return gcd of a and b
function gcd(a, b) {
  if (b === 0) return a;
  return gcd(b, a % b);
}

// Function to return LCM of two numbers
function lcm(a, b) {
  return (a / gcd(a, b)) * b;
}

// Driver program to test above function
const a = 15;
const b = 20;
console.log(`LCM of ${a} and ${b} is ${lcm(a, b)}`);
```

_**Time Complexity:** O(log(min(a,b))_

_**Auxiliary Space:** O(log(min(a,b))_

<mark style="color:red;">**Check for Prime**</mark>\


### What are prime numbers?

* A prime number is a natural number greater than **1**, which is only divisible by 1 and itself. First few prime numbers are: 2 3 5 7 11 13 17 19 23…..
* In other words, the prime number is a positive integer greater than 1 that has exactly two factors, 1 and the number itself.
* There are many prime numbers, such as 2, 3, 5, 7, 11, 13, etc.&#x20;
* Keep in mind that 1 cannot be either prime or composite.&#x20;
* The remaining numbers, except for 1, are classified as prime and composite numbers.

### **Some interesting facts about Prime numbers:**

* Except for 2, which is the smallest prime number and the only even prime number, all prime numbers are odd numbers.
* Every prime number can be represented in form of **6n + 1** or **6n – 1** except the prime numbers 2 and 3, where n is a natural number.
* 2 and 3 are only two consecutive natural numbers that are prime.
* [Goldbach Conjecture: ](https://en.wikipedia.org/wiki/Goldbach's\_conjecture)Every even integer greater than 2 can be expressed as the sum of two primes.
* [Wilson Theorem](https://www.geeksforgeeks.org/wilsons-theorem/): Wilson’s theorem states that a natural number p > 1 is a prime number if and only if
*

    ```
    (p - 1) ! ≡  -1   mod p 
        OR  (p - 1) ! ≡  (p-1) mod p

    ```
* [Fermat’s Little Theorem](https://en.wikipedia.org/wiki/Fermat's\_little\_theorem): If n is a prime number, then for every a, 1 <= a < n,

```
	an-1 ≡ 1 (mod n)
		OR 
	an-1 % n = 1
```

* [Prime Number Theorem](https://en.wikipedia.org/wiki/Prime\_number\_theorem): The probability that a given, randomly chosen number n is prime is inversely proportional to its number of digits, or to the logarithm of n.
* [Lemoine’s Conjecture](https://www.geeksforgeeks.org/lemoines-conjecture/): Any odd integer greater than 5 can be expressed as a sum of an odd prime (all primes other than 2 are odd) and an even semiprime. A semiprime number is a product of two prime numbers. This is called Lemoine’s conjecture.

### Properties of prime numbers:

* Every number greater than 1 can be divided by at least one prime number.
* Every even positive integer greater than 2 can be expressed as the sum of two primes.
* Except 2, all other prime numbers are odd. In other words, we can say that 2 is the only even prime number.
* Two prime numbers are always coprime to each other.
* Each composite number can be factored into prime factors and individually all of these are unique in nature.

### Prime numbers and co-prime numbers:

It is important to distinguish between prime numbers and co-prime numbers. Listed below are the differences between prime and co-prime numbers.

* A coprime number is always considered as a pair, whereas a prime number is considered as a single number.
* Co-prime numbers are numbers that have no common factor except 1. In contrast, prime numbers do not have such a condition.
* A co-prime number can be either prime or composite, but its greatest common factor (GCF) must always be 1. Unlike composite numbers, prime numbers have only two factors, 1 and the number itself.
* **Example of co-prime:** 13 and 15 are co-primes. The factors of 13 are 1 and 13 and the factors of 15 are 1, 3 and 5. We can see that they have only 1 as their common factor, therefore, they are coprime numbers.
* **Example of prime:** A few examples of prime numbers are 2, 3, 5, 7 and 11 etc.

### **How do we check whether a number is Prime or not?**&#x20;

**Naive Approach:** A naive solution is to iterate through all numbers from 2 to sqrt(n) and for every number check if it divides n. If we find any number that divides, we return false.

Below is the implementation:

Javascript

```javascript
// A school method based JavaScript function to
// check if a number is prime

// function to check whether a number
// is prime or not
function isPrime(n) {
	// Corner case
	if (n <= 1) return false;

	// Check from 2 to square root of n
	for (let i = 2; i <= Math.sqrt(n); i++) {
		if (n % i === 0) return false;
	}

	return true;
}

// Driver Code
console.log(isPrime(11));
```

&#x20;

**Output**

<pre><code><strong> true
</strong></code></pre>

**Time Complexity:** O(sqrt(n))\
**Auxiliary space:** O(1)

**Efficient approach:** To check whether  the number is prime or not follow the below idea:

> _In the previous approach given if the size of the given number is too large then its square root will be also very large, so to deal with large size input we will deal with a few numbers such as 1, 2, 3, and the numbers which are divisible by 2 and 3 in separate cases and for remaining numbers, we will iterate our loop from 5 to sqrt(n) and check for each iteration whether that  (iteration) or (that iteration + 2) divides n or not. If we find any number that divides, we return false._

Below is the implementation for the above idea:

Javascript

```javascript
const isPrime = (n) => {
  if (n <= 1) return false;
  if (n === 2 || n === 3) return true;
  if (n % 2 === 0 || n % 3 === 0) return false;

  for (let i = 5; i <= Math.sqrt(n); i = i + 6)
    if (n % i === 0 || n % (i + 2) === 0) return false;

  return true;
}

console.log(isPrime(11) ? "true" : "false");
```

&#x20;

**Output :**

```
true
```

**Time complexity:** O(sqrt(n))\
**Auxiliary space:** O(1)

Marked as ReadReport An Issue\


<mark style="color:red;">**Prime Factors**</mark>

Prime factor is the factor of the given number which is a [prime number](https://www.geeksforgeeks.org/prime-numbers/). Factors are the numbers you multiply together to get another number. In simple words, prime factor is finding which prime numbers multiply together to make the original number.

**Example:** The prime factors of 15 are 3 and 5 (because 3×5=15, and 3 and 5 are prime numbers).&#x20;

**Some interesting fact about Prime Factor :**&#x20;

1. There is only one (unique!) set of prime factors for any number.
2. In order to maintain this property of unique prime factorizations, it is necessary that the number one, 1, be categorized as neither prime nor composite.
3. Prime factorizations can help us with divisibility, simplifying fractions, and finding common denominators for fractions.
4. [Pollard’s Rho](https://www.geeksforgeeks.org/pollards-rho-algorithm-prime-factorization/) is a prime factorization algorithm, particularly fast for a large [composite number](https://www.geeksforgeeks.org/composite-number/) with small prime factors.
5. Cryptography is the study of secret codes. Prime Factorization is very important to people who try to make (or break) secret codes based on numbers.

**How to print a prime factor of a number?**\
**Naive solution:** \
Given a number n, write a function to print all prime factors of n. For example, if the input number is 12, then output should be “2 2 3” and if the input number is 315, then output should be “3 3 5 7”.

Following are the steps to find all prime factors:&#x20;

1. While _n_ is divisible by 2, print 2 and divide n by 2.
2. After step 1, _n_ must be odd. Now start a loop from i = 3 to square root of _n_. While _i_ divides _n_, print _i_ and divide _n_ by _i_, increment _i_ by 2 and continue.
3. If _n_ is a prime number and is greater than 2, then _n_ will not become 1 by above two steps. So print _n_ if it is greater than 2.

Javascript

```javascript
// Program to print all prime factors in JavaScript

// A function to print all prime factors of a given number n
function primeFactors(n) {
  // Print the number of 2s that divide n
  while (n % 2 === 0) {
    console.log(2);
    n = n / 2;
  }

  // n must be odd at this point. So we can skip
  // one element (Note i = i + 2)
  for (let i = 3; i <= Math.sqrt(n); i = i + 2) {
    // While i divides n, print i and divide n
    while (n % i === 0) {
      console.log(i);
      n = n / i;
    }
  }

  // This condition is to handle the case when n
  // is a prime number greater than 2
  if (n > 2) console.log(n);
}

/* Driver program to test above function */
const n = 315;
primeFactors(n);
```

&#x20;

**Output:**&#x20;

```
3 3 5 7
```

Time Complexity: O(sqrt(n) \* log (n) )

Auxiliary Space: O(1)

&#x20;

**More efficient solution:**

Javascript

```javascript
const printPrimeFactors = n => {
    if(n <= 1) return;
    while(n % 2 === 0) {
        console.log(2);
        n = n / 2;
    }
    while(n % 3 === 0) {
        console.log(3);
        n = n / 3;
    }
    for(let i=5; i*i<=n; i=i+6) {
        while(n % i === 0) {
            console.log(i);
            n = n / i;
        }
        while(n % (i + 2) === 0) {
            console.log(i + 2);
            n = n / (i + 2);
        }
    }
    if(n > 3) console.log(n);
};

const main = () => {
    const n = 315;
    printPrimeFactors(n);
    return 0;
};

main();
```

&#x20;

**Output:**&#x20;

```
3 3 5 7
```

<mark style="color:red;">**All Divisors of a Number**</mark>

Given a natural number n, print all distinct divisors of it.

```javascript
function printDivisors(n) {
  let i = 1;
  for (i = 1; i * i < n; i++) {
    if (n % i == 0) {
      console.log(i);
    }
  }

  for (; i >= 1; i--) {
    if (n % i == 0) {
      console.log(n / i);
    }
  }
}

const n = 100;

printDivisors(n);
```

**Output:**

```
1 2 4 5 10 20 25 50 100 
```

Time Complexity: O(sqrt(n))

&#x20;Auxiliary Space : O(1)

<mark style="color:red;">**Sieve of Eratosthenes**</mark>

Given a number n, print all primes smaller than or equal to n. It is also given that n is a small number.

**Example:**&#x20;

> _**Input :** n =10_\
> _**Output :** 2 3 5 7_&#x20;
>
> _**Input :** n = 20_ \
> _**Output:** 2 3 5 7 11 13 17 19_

The sieve of Eratosthenes is one of the most efficient ways to find all primes smaller than n when n is smaller than 10 million or so.

Following is the algorithm to find all the prime numbers less than or equal to a given integer n by the Eratosthene’s method: \
When the algorithm terminates, all the numbers in the list that are not marked are prime.

**Explanation with Example:**&#x20;

Let us take an example when n = 50. So we need to print all prime numbers smaller than or equal to 50.&#x20;

We create a list of all numbers from 2 to 50.&#x20;

```javascript
// JavaScript program to print all primes smaller than or equal to
// n using Sieve of Eratosthenes

function SieveOfEratosthenes(n) {
    let prime = [];
    for (let i = 0; i <= n; i++) {
        prime[i] = true;
    }

    for (let p = 2; p * p <= n; p++) {
        if (prime[p] === true) {
            for (let i = p * p; i <= n; i += p) {
                prime[i] = false;
            }
        }
    }

    let result = [];
    for (let p = 2; p <= n; p++) {
        if (prime[p]) {
            result.push(p);
        }
    }

    return result;
}

// Driver code
let n = 30;
console.log("Following are the prime numbers smaller than or equal to " + n + ": ");
console.log(SieveOfEratosthenes(n));
```

**Output**

<pre><code><strong>Following are the prime numbers smaller  than or equal to 30
</strong><strong>2 3 5 7 11 13 17 19 23 29 
</strong></code></pre>

**Time Complexity:** O(n\*log(log(n)))\
**Auxiliary Space:** O(n)

<mark style="color:red;">**Computing Power**</mark>

Given two integers **x** and **n**, write a function to compute **xn**. We may assume that x and n are small and overflow doesn’t happen.

#### An Optimized Divide and Conquer Solution:

_The problem can be recursively defined by:_

* _power(x, n) = power(x, n / 2) \* power(x, n / 2);        // if n is even_
* _power(x, n) = x \* power(x, n / 2) \* power(x, n / 2);    // if n is odd_

However there is a problem with the above solution, the same subproblem is computed twice for each recursive call. We can optimize the above function by computing the solution of the subproblem once only.

Below is the implementation of the above approach:

Javascript

```javascript
function power(x, y) {
  if (y === 0) return 1;
  let temp = power(x, Math.floor(y / 2));
  if (y % 2 === 0) return temp * temp;
  else return x * temp * temp;
}

let x = 2;
let y = 3;

console.log(power(x, y));
```

&#x20;

**Output**

```
8
```

**Time Complexity:** O(log n)\
**Auxiliary Space:** O(log n), for recursive call stack

<mark style="color:red;">**Iterative Power**</mark>

Given an integer x and a positive number y, write a function that computes xy under following conditions. \
a) Time complexity of the function should be O(Log y) \
b) Extra Space is O(1)&#x20;

**Examples:**&#x20;

```
Input: x = 3, y = 5
Output: 243

Input: x = 2, y = 5
Output: 32
```

The recursive solutions are generally not preferred as they require space on call stack and they involve function call overhead.&#x20;

Following is implementation to compute xy. &#x20;

Javascript

```javascript
function power(x, y) {
  let res = 1;
  while (y > 0) {
    if (y & 1) {
      res = res * x;
    }
    y = y >> 1;
    x = x * x;
  }
  return res;
}

const x = 3;
const y = 5;

console.log("Power is " + power(x, y));
```

&#x20;

**Output:**&#x20;

```
Power is 243
```

_**Time Complexity:** O(log y), since in loop each time the value of y decreases by half it’s current value._

_**Auxiliary Space:** O(1), since no extra space has been taken._

<mark style="color:red;">**Recursion Basics**</mark>

**What is Recursion?**

The process in which a function calls itself directly or indirectly is called recursion and the corresponding function is called as recursive function. Using recursive algorithm, certain problems can be solved quite easily. Examples of such problems are [Towers of Hanoi (TOH)](http://quiz.geeksforgeeks.org/c-program-for-tower-of-hanoi/), [Inorder/Preorder/Postorder Tree Traversals](https://www.cdn.geeksforgeeks.org/tree-traversals-inorder-preorder-and-postorder/), [DFS of Graph](https://www.cdn.geeksforgeeks.org/depth-first-traversal-for-a-graph/), etc.\


**What is the base condition in recursion?**

In a recursive program, the solution to the base case is provided and the solution of bigger problem is expressed in terms of smaller problems.

```
function fact(n) {
    if (n <= 1) { // base case
        return 1;
    } else {
        return n * fact(n - 1);
    }
}
```

In the above example, the base case for n < = 1 is defined and a larger value of a number can be solved by converting to a smaller one till the base case is reached.

**How a particular problem is solved using recursion?**

\
The idea is to represent a problem in terms of one or more smaller problems, and add one or more base conditions that stop recursion. For example, we compute factorial n if we know factorial of (n-1). The base case for factorial would be n = 0. We return 1 when n = 0. \
\
**Why Stack Overflow error occurs in recursion?**\
If the base case is not reached or not defined, then the stack overflow problem may arise. Let us take an example to understand this.

```
function fact(n)
{
    // wrong base case (it may cause
    // stack overflow).
    if (n == 100) 
        return 1;

    else
        return n*fact(n-1);
}
```

If fact(10) is called, it will call fact(9), fact(8), fact(7), and so on but the number will never reach 100. So, the base case is not reached. If the memory is exhausted by these functions on the stack, it will cause a stack overflow error.

**How memory is allocated to different function calls in recursion?**

When any function is called from main(), the memory is allocated to it on stack. A recursive function calls itself, the memory for the called function is allocated on top of memory allocated to the calling function and a different copy of local variables is created for each function call. When the base case is reached, the function returns its value to the function by whom it is called and memory is de-allocated and the process continues. Let us take the example of how recursion works by taking a simple function:

```
function printFun(test)

{

    if (test < 1)

        return;

    else

    {

        print test;

        printFun(test-1);    // statement 2

        print test;

        return;

    }

}



// Calling function printFun()

var test = 3;

printFun(test);
```

**Output** :

```
3 2 1 1 2 3
```

When **printFun(3)** is called from main(), memory is allocated to **printFun(3)** and a local variable test is initialized to 3 and statement 1 to 4 are pushed on the stack as shown in below diagram. It first prints ‘3’. In statement 2, **printFun(2)** is called and memory is allocated to **printFun(2)** and a local variable test is initialized to 2 and statements 1 to 4 are pushed in the stack. Similarly, **printFun(2)** calls **printFun(1)** and **printFun(1)** calls **printFun(0)**. **printFun(0)** goes to if statement and it returns to **printFun(1)**. Remaining statements of **printFun(1)** are executed and it returns to **printFun(2)** and so on. In the output, values from 3 to 1 are printed and then 1 to 3 are printed.&#x20;

&#x20;**Disadvantage of Recursion**: Note that both recursive and iterative programs have the same problem-solving powers, i.e., every recursive program can be written iteratively and vice versa. Recursive program has greater space requirements than iterative program as all functions will remain in the stack until the base case is reached. A recursive program also has greater time requirements because of function calls and return overhead. **Advantages of Recursion**: Recursion provides a clean and simple way to write code. Some problems are inherently recursive like tree traversals, Tower of Hanoi, etc. For such problems, it is preferred to write recursive code. We can write such codes also iteratively with the help of the stack data structure.

Applications of Recursion

***

Recursion is a powerful concept in computer programming that allows us to solve problems in a cleaner and more elegant way. Recursion is often used when a task can be broken down into smaller, repetitive tasks. In this article, we'll discuss some common applications of recursion in JavaScript and provide code examples to help illustrate these concepts.

1. Factorial Calculation

One of the most common examples of recursion is calculating the factorial of a number. Factorial is the product of all positive integers up to and including a given number. For example, the factorial of 5 is 5 \* 4 \* 3 \* 2 \* 1 = 120.

Here's an example of a recursive function in JavaScript that calculates the factorial of a number:

```
javascriptCopy codefunction factorial(n) {
  if (n === 0) {
    return 1;
  } else {
    return n * factorial(n - 1);
  }
}
```

1. Traversing a Tree Structure

Another common application of recursion is traversing a tree structure. A tree is a hierarchical data structure that consists of nodes and edges. Each node in a tree has a parent node and zero or more child nodes. Recursion can be used to traverse a tree and perform operations on each node.

Here's an example of a recursive function in JavaScript that performs a pre-order traversal of a binary tree:

```
scssCopy codefunction preOrderTraversal(node) {
  if (!node) {
    return;
  }
  console.log(node.value);
  preOrderTraversal(node.left);
  preOrderTraversal(node.right);
}
```

1. Generating Permutations and Combinations

Recursion can also be used to generate all permutations and combinations of a given set of elements. For example, we can use recursion to generate all possible combinations of a given set of characters.

Here's an example of a recursive function in JavaScript that generates all permutations of a given string:

```
rustCopy codefunction permutations(str) {
  if (str.length === 1) {
    return [str];
  }
  const result = [];
  for (let i = 0; i < str.length; i++) {
    const firstChar = str[i];
    const otherChars = str.substring(0, i) + str.substring(i + 1);
    const otherPermutations = permutations(otherChars);
    for (const permutation of otherPermutations) {
      result.push(firstChar + permutation);
    }
  }
  return result;
}
```

In conclusion, recursion is a powerful concept that allows us to solve problems in a cleaner and more elegant way. Whether we're calculating a factorial, traversing a tree structure, or generating permutations and combinations, recursion can help us write more efficient and maintainable code.

**Approach 2:** We will use [recursion](https://www.geeksforgeeks.org/recursion/) to solve this problem.\
&#x20;

1. Check for the base case. Here it is N<=0.
2. If base condition satisfied, return to the main function.
3. If base condition not satisfied, print N and call the function recursively with value (N – 1) until base condition satisfies.

Below is the implementation of the above approach.&#x20;

Javascript

```javascript
// Recursive function to print from N to 1
function printReverseOrder(N) {
  if (N <= 0) {
    return;
  } else {
    console.log(N);

    // recursive call of the function
    printReverseOrder(N - 1);
  }
}

// Driver code
(function main() {
  const N = 5;

  printReverseOrder(N);
})();
```

\
**Output**

```
5 4 3 2 1 
```

**Time Complexity:** O(N)

**Auxiliary Space:** O(N)

Tail Recursion

***

As we read before, that recursion is defined when a function invokes/calls itself.\
\
**Tail Recursion**: A recursive function is said to be following Tail Recursion if it invokes itself at the end of the function. That is, if all of the statements are executed before the function invokes itself then it is said to be following Tail Recursion.\
\
**For Example**:\
&#x20;

Javascript

```javascript
function printN(N) {
  if (N === 0) {
    return;
  } else {
    console.log(N);
    printN(N - 1);
  }
}
```

The above function call for **N = 5** will print:\
&#x20;

```
5 4 3 2 1
```

\
\
&#x20;

**Which one is Better-Tail Recursive or Non Tail-Recursive?**

\
The tail-recursive functions are considered better than non-tail recursive functions as tail-recursion can be optimized by the compiler. The idea used by compilers to optimize tail-recursive functions is simple, since the recursive call is the last statement, there is nothing left to do in the current function, so saving the current function’s stack frame is of no use.\
\
\
&#x20;

**Can a non-tail recursive function be written as tail-recursive to optimize it?**

\
Consider the following function to calculate factorial of N. Although it looks like Tail Recursive at first look, it is a non-tail-recursive function. If we take a closer look, we can see that the value returned by **fact(N-1)** is used in **fact(N)**, so the call to fact(N-1) is not the last thing done by fact(N).\
&#x20;

```
function fact( N) 
{ 
    if (N === 0) 
        return 1; 
  
    return N*fact(N-1); 
} 
```

\
The above function can be written as a Tail Recursive function. The idea is to use one more argument and accumulate the factorial value in the second argument. When N reaches 0, return the accumulated value.\
&#x20;

```
function factTR(N, a) 
{ 
    if (N === 0)  
        return a; 
  
    return factTR(N-1, N*a); 
} 
```

Marked as ReadReport An Issue\
\
<mark style="color:red;">**Natural Number Sum using Recursion**</mark>

Given a number n, find sum of first _n_ natural numbers. To calculate the sum, we will use a recursive function recur\_sum().\
**Examples :** \
&#x20;

```
Input : 3
Output : 6
Explanation : 1 + 2 + 3 = 6

Input : 5
Output : 15
Explanation : 1 + 2 + 3 + 4 + 5 = 15
```

\
Below is code to find the sum of natural numbers up to n using recursion : \
&#x20;

Javascript

```javascript
// Returns sum of first n natural numbers
function recurSum(n) {
  if (n <= 1) {
    return n;
  }
  return n + recurSum(n - 1);
}

// Driver code
(function main() {
  const n = 5;
  console.log(recurSum(n));
})();
```

**Output :**&#x20;

```
15 
```

**Time complexity :** O(n)

**Auxiliary space :** O(n)

<mark style="color:red;">**Palindrome Check using Recursion**</mark>

***

Given a string, write a recursive function that checks if the given string is a palindrome, else, not a palindrome.

```
Input : malayalam
Output : Yes
Reverse of malayalam is also
malayalam.

Input : max
Output : No
Reverse of max is not max. 
```

```javascript
const isPalindrome = (s, i) => {
  if (i > s.length / 2) {
    return true;
  }

  return s[i] === s[s.length - i - 1] && isPalindrome(s, i + 1);
};

const main = () => {
  const str = "geeg";
  if (isPalindrome(str, 0)) {
    console.log("Yes");
  } else {
    console.log("No");
  }

  return 0;
};

main();
```

**Time Complexity:** O(n)\
**Auxiliary Space:** O(n)

<mark style="color:red;">**Sum of Digits Using Recursion**</mark>

Given a number, we need to find sum of its digits using recursion.\
Examples: \
&#x20;

```
Input : 12345
Output : 15

Input : 45632
Output :20
          
```

\
The step-by-step process for a better understanding of how the algorithm works. \
Let the number be 12345. \
Step 1-> 12345 % 10 which is equal-too 5 + ( send 12345/10 to next step ) \
Step 2-> 1234 % 10 which is equal-too 4 + ( send 1234/10 to next step ) \
Step 3-> 123 % 10 which is equal-too 3 + ( send 123/10 to next step ) \
Step 4-> 12 % 10 which is equal-too 2 + ( send 12/10 to next step ) \
Step 5-> 1 % 10 which is equal-too 1 + ( send 1/10 to next step ) \
Step 6-> 0 algorithm stops \
following diagram will illustrate the process of recursion&#x20;

```javascript
// Recursive JavaScript program to find sum of digits of a number

function sumOfDigit(n) {
  if (n === 0) return 0;
  return (n % 10 + sumOfDigit(Math.floor(n / 10)));
}

// Driver code
const num = 12345;
const result = sumOfDigit(num);
console.log(`Sum of digits in ${num} is ${result}`);
```

**Time complexity :** O(logn) where n is the given number.&#x20;

**Auxiliary space :** O(logn) due to recursive stack space.\
