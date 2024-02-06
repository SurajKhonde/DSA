# FastTag

<mark style="color:red;">**Math**</mark>

### **count digits in an integer**

1. After the first iteration, the value of n will be updated to 345 and the count is incremented to 1.
2. After the second iteration, the value of n will be updated to 34 and the count is incremented to 2.
3. After the third iteration, the value of n will be updated to 3 and the count is incremented to 3.
4. In the fourth iteration, the value of n will be updated to zero and the count will be incremented to 4. &#x20;
5. Then the test expression is evaluated ( n!=0 ) as false and the loop terminates with final count as 4

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

<mark style="color:red;">**Palindrome Numbers**</mark>

To check whether the given number is palindrome or not we will just reverse the digits of the given number and check if the reverse of that number is equal to the original number or not .

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

<mark style="color:red;">**Factorial of a Number**</mark>

* Factorial of a non-negative integer is the multiplication of all positive integers smaller than or equal to n. For example factorial of 6 is 6\*5\*4\*3\*2\*1 which is 720.&#x20;

```javascript
function factorial(n) {
  if (n === 0 || n === 1) return 1;
  return n * factorial(n - 1);
}

const num = 5;
console.log(`Factorial of ${num} is ${factorial(num)}`);
```

### **Iterative Solution to find factorial of a number**

```javascript
function factorial(n) {
  let res = 1;
  for (let i = 2; i <= n; i++) res *= i;
  return res;
}

const num = 5;
console.log(`Factorial of ${num} is ${factorial(num)}`);
```

<mark style="color:red;">**Trailing Zeros in Factorial**</mark>&#x20;

1. **Approach:**\
   A simple method is to first calculate factorial of n, then count trailing 0s in the result (We can count trailing 0s by repeatedly dividing the factorial by 10 till the remainder is 0).\
   &#x20;
2. The above method can cause overflow for slightly bigger numbers as the factorial of a number is a big number (See factorial of 20 given in above examples). The idea is to consider prime factors of a factorial n. A trailing zero is always produced by prime factors 2 and 5. If we can count the number of 5s and 2s, our task is done. Consider the following examples.\
   **n = 5:** There is one 5 and 3 2s in prime factors of 5! (2 \* 2 \* 2 \* 3 \* 5). So a count of trailing 0s is 1.\
   **n = 11:** There are two 5s and eight 2s in prime factors of 11! (2 8 \* 34 \* 52 \* 7). So the count of trailing 0s is 2.\
   &#x20;
3. We can easily observe that the number of 2s in prime factors is always more than or equal to the number of 5s. So if we count 5s in prime factors, we are done. _How to count_ the _total number of 5s in prime factors of n!?_ A simple way is to calculate floor(n/5). For example, 7! has one 5, 10! has two 5s. It is not done yet, there is one more thing to consider. Numbers like 25, 125, etc have more than one 5. For example, if we consider 28! we get one extra 5 and the number of 0s becomes 6. Handling this is simple, first, divide n by 5 and remove all single 5s, then divide by 25 to remove extra 5s, and so on. Following is the summarized formula for counting trailing 0s.

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

<mark style="color:red;">**GCD or HCF of two Numbers**</mark>

```javascript
const gcd = (a, b) => {
  return b === 0 ? a : gcd(b, a % b);
};

const a = 98, b = 56;
console.log(`GCD of ${a} and ${b} is ${gcd(a, b)}`);
```

**Time Complexity:** O(log(min(a,b))|\
**Auxiliary Space:** O(log(min(a,b))\


<mark style="color:red;">**LCM of Two Numbers**</mark>

LCM (Least Common Multiple) of two numbers is the smallest number which can be divided by both numbers.&#x20;

For example, LCM of 15 and 20 is 60, and LCM of 5 and 7 is 35.

A **simple solution** is to find all prime factors of both numbers, then find union of all factors present in both numbers. Finally, return the product of elements in union.

An **efficient solution** is based on the below formula for LCM of two numbers ‘a’ and ‘b’.&#x20;

```
   a x b = LCM(a, b) * GCD (a, b)

   LCM(a, b) = (a x b) / GCD(a, b)
```

We have discussed function to find GCD of two numbers. Using GCD, we can find LCM.&#x20;

```javascript
// JavaScript program to find LCM of two numbers

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

Marked as ReadReport An Issue\


<mark style="color:red;">**Check for Prime**</mark>

* In other words, the prime number is a positive integer greater than 1 that has exactly two factors, 1 and the number itself.
* There are many prime numbers, such as 2, 3, 5, 7, 11, 13, etc.&#x20;
* Keep in mind that 1 cannot be either prime or composite.&#x20;
* The remaining numbers, except for 1, are classified as prime and composite numbers.&#x20;

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

**Time complexity:** O(sqrt(n))\
**Auxiliary space:** O(1)

<mark style="color:red;">**Prime Factors**</mark>

**Example:** The prime factors of 15 are 3 and 5 (because 3×5=15, and 3 and 5 are prime numbers).&#x20;

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

<mark style="color:red;">**All Divisors of a Number**</mark>

```javascript
const printDivisors = (n) => {
  for (let i = 1; i <= Math.sqrt(n); i++) {
    if (n % i === 0) {
      if (n / i === i) {
        console.log(i);
      } else {
        console.log(i, n / i);
      }
    }
  }
};

console.log("The divisors of 100 are:");
printDivisors(100);
```

**Printing all the divisors in sorted order:**

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

Time Complexity: O(sqrt(n)) Auxiliary Space : O(1)



<mark style="color:red;">**Sieve of Eratosthenes**</mark>

The sieve of Eratosthenes is one of the most efficient ways to find all primes smaller than n when n is smaller than 10 million or so.

```javascript
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

<mark style="color:red;">**Computing Power**</mark>

```javascript
function power(x, n) {
  let pow = 1;
  for (let i = 0; i < n; i++) {
    pow = pow * x;
  }
  return pow;
}

// Driver code
let x = 2;
let n = 3;

// Function call
let result = power(x, n);
console.log(result);
```

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

<mark style="color:red;">**Iterative Power**</mark>

Given an integer x and a positive number y, write a function that computes xy under following conditions. a) Time complexity of the function should be O(Log y) b) Extra Space is O(1)

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

_**Time Complexity:** O(log y), since in loop each time the value of y decreases by half it’s current value._

_**Auxiliary Space:** O(1), since no extra space has been taken_



<mark style="color:red;">Recursion Basics</mark>

```
function fact(n) {
    if (n <= 1) { // base case
        return 1;
    } else {
        return n * fact(n - 1);
    }
}
```

Given a quadratic equation in the form **ax2 + bx + c**. Find its roots.

**Note:** Return the maximum root followed by the minimum root.

#### <mark style="color:orange;">Max and Second Ma</mark>x

Given an array **arr**\[] of size **N** of positive integers which may have duplicates. The task is to find the **maximum** and **second maximum** from the array, and both of them should be **different from each other**, so If **no second max** exists, then the **second max** will be **-1**.

<pre><code><strong>Input:
</strong>N = 3
arr[] = {2,1,2}
<strong>Output: 2 1
</strong><strong>Explanation: From the given array 
</strong>elements, 2 is the largest and 1 
is the second largest.
</code></pre>



```javascript
largestAndSecondLargest(sizeOfArray, arr)
    {
        let max = -1;
    let secondMax = -1;

    for (let i = 0; i < sizeOfArray ; i++) {
        if (arr[i] > max) {
            secondMax = max;
            max = arr[i];
        } else if (arr[i] > secondMax && arr[i] !== max) {
            secondMax = arr[i];
        }
    }

    return [max, secondMax];
    }
```

