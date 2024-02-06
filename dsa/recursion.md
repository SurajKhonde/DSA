---
cover: >-
  https://images.unsplash.com/photo-1684395646154-19832d6265b3?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwxfHxSZWN1cnNpb24lMjB8ZW58MHx8fHwxNzA3MjIxMDc4fDA&ixlib=rb-4.0.3&q=85
coverY: 0
---

# Recursion

**What is Recursion?**

\
The process in which a function calls itself directly or indirectly is called recursion and the corresponding function is called as recursive function. Using recursive algorithm, certain problems can be solved quite easily. Examples of such problems are [Towers of Hanoi (TOH)](http://quiz.geeksforgeeks.org/c-program-for-tower-of-hanoi/), [Inorder/Preorder/Postorder Tree Traversals](https://www.cdn.geeksforgeeks.org/tree-traversals-inorder-preorder-and-postorder/), [DFS of Graph](https://www.cdn.geeksforgeeks.org/depth-first-traversal-for-a-graph/), etc.\
\
\
&#x20;

**What is the base condition in recursion?**

\
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

**How a particular problem is solved using recursion?**

\
The idea is to represent a problem in terms of one or more smaller problems, and add one or more base conditions that stop recursion. For example, we compute factorial n if we know factorial of (n-1). The base case for factorial would be n = 0. We return 1 when n = 0. \
\
**Why Stack Overflow error occurs in recursion?**\
If the base case is not reached or not defined, then the stack overflow problem may arise. Let us take an example to understand this.\
&#x20;

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

\
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

Print N to 1 Using Recursion

***

Given a number **N**, the task is to print the numbers from **N to 1**.\
**Examples:**&#x20;

> _**Input:** N = 10_ \
> _**Output:** 10 9 8 7 6 5 4 3 2 1_\
> _**Input:** N = 7_ \
> _**Output:** 7 6 5 4 3 2 1_  &#x20;

**Approach 1:** Run a loop from N to 1 and print the value of N for each iteration. Decrement the value of N by 1 after each iteration.\
Below is the implementation of the above approach.&#x20;

Javascript

```javascript
// Recursive function to print from N to 1
function printReverseOrder(N) {
  for (let i = N; i > 0; i--) {
    console.log(i);
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

_**Time Complexity:** O(N)_

_**Auxiliary Space:** O(1)_

&#x20;

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

Print 1 to N Using Recursion

***

Given a number **N**, the task is to print the numbers from **N to 1**.

\
**Examples:**&#x20;

> _**Input:** N = 10_ \
> _**Output:** 1 2 3 4 5 6 7 8 9 10_\
> _**Input:** N = 7_ \
> _**Output:** 1 2 3 4 5 6 7_

&#x20;

**Method-1:**

Javascript

```javascript
class GFG {
  // It prints numbers from 1 to n.
  printNos(n) {
    if (n > 0) {
      this.printNos(n - 1);
      console.log(n);
    }
    return;
  }
}

// Driver code
(function main() {
  const g = new GFG();
  g.printNos(10);
})();
```

\
**Output**

```
1 2 3 4 5 6 7 8 9 10 
```

_**Time Complexity:** O(n)_

_**Auxiliary Space:** O(n)_

&#x20;

**Method 2:**

Javascript

```javascript
function printNos(initial, last) {
  if (initial <= last) {
    console.log(initial);
    printNos(initial + 1, last);
  }
}

(function main() {
  printNos(1, 10);
})();
```

\
**Output**

```
1 2 3 4 5 6 7 8 9 10 
```

**Time Complexity :** O(n)

_**Auxiliary Space:** O(n)_

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

<mark style="color:red;">**Natural Number Sum using Recursion**</mark>\


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

\
<mark style="color:red;">**Palindrome Check using Recursion**</mark>

***

Given a string, write a recursive function that checks if the given string is a palindrome, else, not a palindrome.

**Examples:**&#x20;

```
Input : malayalam
Output : Yes
Reverse of malayalam is also
malayalam.

Input : max
Output : No
Reverse of max is not max. 
```

&#x20;

The idea of a recursive function is simple:&#x20;

```
1) If there is only one character in string
   return true.
2) Else compare first and last characters
   and recur for remaining substring.
```

Below is the implementation of the above idea:&#x20;



```javascript
// A recursive function that
// check a str.substring(s, e) is
// palindrome or not.
function isPalRec(str, s, e) {
    // If there is only one character
    if (s === e) return true;

    // If first and last characters do not match
    if (str[s] !== str[e]) return false;

    // If there are more than two characters, check if 
    // middle substring is also palindrome or not.
    if (s < e + 1) return isPalRec(str, s + 1, e - 1);

    return true;
}

function isPalindrome(str) {
    let n = str.length;

    // An empty string is considered as palindrome
    if (n === 0) return true;

    return isPalRec(str, 0, n - 1);
}

// Driver Code
let str = "geeg";

if (isPalindrome(str)) console.log("Yes");
else console.log("No");
```

\
**Output**

```
Yes
```

**Time Complexity:** O(n)\
**Auxiliary Space:** O(n)

**Another Approach :**

Basically while traversing check whether ith and n-i-1th index are equal or not.

If there are not equal return false and if they are equal then continue with the recursion calls.

Javascript

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

\
**Output**

```
Yes
```

**Time Complexity:** O(n)\
**Auxiliary Space:** O(n)

Sum of Digits Using Recursion

***

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
following diagram will illustrate the process of recursion \
&#x20;

![](https://media.geeksforgeeks.org/wp-content/uploads/1-37-e1513491182807.png)

\
&#x20;

Javascript

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

**Output:**&#x20;

```
Sum of digits in 12345 is 15
```

Besides writing (n==0 , then return 0) in the code given above we can also write it in this manner , there will be no change in the output .

```
if(n<10) return n; By writing this there will be no need to 
call the function for the numbers which are less than 10 
```

**Time complexity :** O(logn) where n is the given number.&#x20;

**Auxiliary space :** O(logn) due to recursive stack space.

