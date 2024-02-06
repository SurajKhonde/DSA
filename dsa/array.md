---
description: Array and Object are the backbone
cover: >-
  https://images.unsplash.com/photo-1561117089-3fb7c944887f?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwzfHxBcnJheXxlbnwwfHx8fDE3MDcxOTQ0OTR8MA&ixlib=rb-4.0.3&q=85
coverY: 0
---

# Array

Introduction to Arrays

***

### What is an Array?

> _An **array** is a collection of items of the same variable type stored that are stored at contiguous memory locations. It’s one of the most popular and simple data structures and is often used to implement other data structures. Each item in an array is indexed starting with 0._

The dream of every programmer is to become not just a good, but also a great programmer. We all want to achieve our goals and to achieve our goals, we must have a great plan with us. In this context, we have decided to provide a complete guide for Arrays interview preparation, which will help you to tackle the problems that are mostly asked in the interview, such as What is an Array, What is Array in C language, How do you initialize an Array in C, How to sort an Array, etc. We have also covered the topics such as Top **Theoretical interview questions** and **Top interview coding questions** in this complete guide for Array interview preparation.

We can directly access an array element by using its index value.

### Basic terminologies of array

* **Array Index:** In an array, elements are identified by their indexes. Array index starts from 0.
* **Array element:** Elements are items stored in an array and can be accessed by their index.
* **Array Length:** The length of an array is determined by the number of elements it can contain.&#x20;

### Representation of Array

The representation of an array can be defined by its declaration. A declaration means allocating memory for an array of a given size.

Arrays can be declared in various ways in different languages. For better illustration, below are some language-specific array declarations.

Javascript

```javascript
var arr = new Array(5); // This array will store integer type element
var arr = new Array(10); // This array will store char type element
var arr = new Array(20); // This array will store float type element
```

&#x20;

However, the above declaration is **static** or **compile-time** memory allocation, which means that the array element’s memory is allocated when a program is compiled. Here only a fixed size (i,e. the size that is mentioned in square brackets **\[]**) of memory will be allocated for storage, but don’t you think it will not be the same situation as we know the size of the array every time, there might be a case where we don’t know the size of the array. If we declare a larger size and store a lesser number of elements will result in a wastage of memory or either be a case where we declare a lesser size then we won’t get enough memory to store the rest of the elements. In such cases, static memory allocation is not preferred.

### **Why Array Data Structures is needed?**

Assume there is a class of five students and if we have to keep records of their marks in examination then, we can do this by declaring five variables individual and keeping track of records but what if the number of students becomes very large, it would be challenging to manipulate and maintain the data.

What it means is that, we can use normal variables (v1, v2, v3, ..) when we have a small number of objects. But if we want to store a large number of instances, it becomes difficult to manage them with normal variables. **The idea of an array is to represent many instances in one variable**..

Implementing Arrays in Javascript

***

JavaScript array is a single variable that is used to store different elements. It is often used when we want to store a list of elements and access them by a single variable. Unlike most languages where the array is a reference to the multiple variables, in JavaScript, an array is a single variable that stores multiple elements.

### Why do we use arrays?

Arrays help to store multiple values with the same data type in the name of a single variable, otherwise, we have to declare separate variables for each value. However, if you want to loop over a larger number of elements then it is efficient to store the values in an array, instead of writing the same code for each value again and again.

<mark style="color:red;">**Largest Element in an Array**</mark>

Given an array **arr** of size **N**, the task is to find the largest element in the given array.&#x20;

**Example:**&#x20;

> _**Input:** arr\[] = {10, 20, 4}_\
> _**Output:** 20_
>
> _**Input :** arr\[] = {20, 10, 20, 4, 100}_\
> _**Output :** 100_

**Approach 1 - Naive Method:**

```javascript
function getLargest(arr, n) {
    for (let i = 0; i < n; ++i) {
        let flag = true;
        for (let j = i; j < n; ++j) {
            if (arr[j] > arr[i]) {
                flag = false;
                break;
            }
        }
        if (flag) {
            return arr[i];
        }
    }
    return -1;
}

let arr = [5, 8, 20, 15];
console.log("Largest in given array is " + getLargest(arr, 4));
```

**Approach 2 – Linear Traversal:** One of the most simplest and basic approach to solve this problem is to simply traverse the whole list and find the maximum among them.&#x20;

Follow the steps below to implement this idea:

* Create a local variable **max** to store the maximum among the list
* **Initialize max with the first element** initially, to start the comparison.
* Then **traverse the given array** from second element till end, and for each element:
  * **Compare the current element with max**
  * If the current element is greater than max, then **replace** the value of **max** with the current element.
* At the end, **return** and print the value of the largest element of array stored in **max**.

Below is the implementation of the above approach:&#x20;

Javascript

```javascript
function largest(arr) {
    let max = arr[0];
    for (let i = 1; i < arr.length; i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
    }
    return max;
}

let arr = [10, 324, 45, 90, 9808];
console.log("Largest in given array is " + largest(arr));
```

<mark style="color:orange;">**Second Largest Element in Array**</mark>

***

Given an array of integers, our task is to write a program that efficiently finds the second largest element present in the array.

**Efficient Solution:**

**Approach:** Find the second largest element in a single traversal. \
Below is the complete algorithm for doing this: &#x20;

```
1) Initialize the first as 0(i.e, index of arr[0] element
2) Start traversing the array from array[1],
   a) If the current element in array say arr[i] is greater
      than first. Then update first and second as,
      second = first
      first = arr[i]
   b) If the current element is in between first and second,
      then update second to store the value of current variable as
      second = arr[i]
3) Return the value stored in second.
```

```javascript
function secondLargest(arr) {
    let first = 0, second = -1;
    for (let i = 1; i < arr.length; i++) {
        if (arr[i] > arr[first]) {
            second = first;
            first = i;
        } else if (arr[i] < arr[first]) {
            if (second === -1 || arr[second] < arr[i]) {
                second = i;
            }
        }
    }
    return second;
}

let arr = [10, 12, 20, 4];
let index = secondLargest(arr);
if (index === -1) {
    console.log("Second Largest didn't exist");
} else {
    console.log("Second largest : " + arr[index]);
}
```

&#x20;

**Output**

```
The second largest element is 34
```

**Complexity Analysis:**

* **Time Complexity: O(n).** \
  Only one traversal of the array is needed.
* **Auxiliary space:** **O(1).** \
  As no extra space is required.

<mark style="color:red;">**Check if an array is sorted**</mark>

***

Given an array of size **n**, write a program to check if it is sorted in ascending order or not. Equal values are allowed in an array and two consecutive equal values are considered sorted.

Given an array of size **n**, write a program to check if it is sorted in ascending order or not. Equal values are allowed in an array and two consecutive equal values are considered sorted.

**Examples:**&#x20;

```
Input : 20 21 45 89 89 90
Output : Yes

Input : 20 20 45 89 89 90
Output : Yes

Input : 20 20 78 98 99 97
Output : No
```

**Iterative approach:**

Javascript

```javascript
function arraySortedOrNot(arr) {
    if (arr.length === 0 || arr.length === 1) {
        return true;
    }
    for (let i = 1; i < arr.length; i++) {
        if (arr[i - 1] > arr[i]) {
            return false;
        }
    }
    return true;
}

let arr = [20, 23, 23, 45, 78, 88];
if (arraySortedOrNot(arr)) {
    console.log("Yes");
} else {
    console.log("No");
}
```

&#x20;

**Output**

```
Yes
```

**Time Complexity: O(n)** \
**Auxiliary Space: O(1)**

Reverse an Array

***

Given an array (or string), the task is to reverse the array/string.

**Iterative way :**

_1) Initialize start and end indexes as start = 0, end = n-1_ \
_2) In a loop, swap arr\[start] with arr\[end] and change start and end as follows :_ \
_start = start +1, end = end – 1_

```javascript
function reverseArray(arr, start, end) {
    while (start < end) {
        let temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        start++;
        end--;
    }
}

function printArray(arr) {
    console.log(arr.join(" "));
}

let arr = [1, 2, 3, 4, 5, 6];

console.log("Original array: ");
printArray(arr);

reverseArray(arr, 0, arr.length - 1);

console.log("Reversed array: ");
printArray(arr);
```

&#x20;

**Output :**&#x20;

```
1 2 3 4 5 6 
Reversed array is 
6 5 4 3 2 1 
```

**Time Complexity :** O(n)

<mark style="color:red;">**Move Zeros to End**</mark>

Given an array of **n** numbers. The problem is to move all the 0’s to the end of the array while maintaining the order of the other elements. Only single traversal of the array is required.\
Examples: \
&#x20;

```
Input : arr[]  = {1, 2, 0, 0, 0, 3, 6}
Output : 1 2 3 6 0 0 0

Input: arr[] = {0, 1, 9, 8, 4, 0, 0, 2, 7, 0, 6, 0, 9}
Output: 1 9 8 4 2 7 6 9 0 0 0 0 0
```

**Algorithm:** \
&#x20;

```
moveZerosToEnd(arr, n)
    Initialize count = 0
    for i = 0 to n-1
        if (arr[i] != 0) then
            arr[count++]=arr[i]
    for i = count to n-1
        arr[i] = 0
```

Javascript

```javascript
function moveZerosToEnd(arr) {
    // Count of non-zero elements
    let count = 0;

    // Traverse the array. If arr[i] is non-zero, then
    // update the value of arr at index count to arr[i]
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] !== 0) {
            arr[count++] = arr[i];
        }
    }

    // Update all elements at index >=count with value 0
    for (let i = count; i < arr.length; i++) {
        arr[i] = 0;
    }

    // print the modified array
    console.log("Modified array: " + arr);
}

// test the function
let testArr = [0, 1, 9, 8, 4, 0, 0, 2, 7, 0, 6, 0, 9];
console.log("Original array: " + testArr);
moveZerosToEnd(testArr);
```

&#x20;

**Output**

```
Original array: 0 1 9 8 4 0 0 2 7 0 6 0 9 
Modified array: 1 9 8 4 2 7 6 9 0 0 0 0 0 
```

Time Complexity: O(n). \
Auxiliary Space: O(1).

<mark style="color:red;">**Remove duplicates from a sorted array**</mark>

***

Given a sorted array, the task is to remove the duplicate elements from the array.

**Method 2:** (Constant extra space)

Javascript

```javascript
function remDups(arr) {
    let res = 1;
    for (let i = 1; i < arr.length; i++) {
        if (arr[res - 1] !== arr[i]) {
            arr[res] = arr[i];
            res++;
        }
    }
    return res;
}

let arr = [10, 20, 20, 30, 30, 30];
console.log("Before Removal: " + arr);
let n = remDups(arr);
console.log("After Removal: " + arr.slice(0,n));
```

&#x20;

**Output**

<pre><code><strong>Before Removal
</strong><strong>10 20 20 30 30 30 
</strong><strong>After Removal
</strong><strong>10 20 30 
</strong></code></pre>

**Time Complexity : O(n)** \
**Auxiliary Space : O(1)**

<mark style="color:red;">**Left Rotate an Array by One**</mark>

Given an array of integers **arr\[]** of size **N** and an integer, the task is to rotate the array elements to the **left** by one position.

**Examples:** &#x20;

> _**Input:**_ \
> _arr\[] = {1, 2, 3, 4, 5, 6, 7}_\
> _**Output:** 2 3 4 5 6 7 1_
>
> _**Input:** arr\[] = {3, 4, 5, 6, 7, 1, 2}_\
> _**Output:** 4 5 6 7 1 2 3_

_**Implementation:**_

Javascript

```javascript
function lRotateOne(arr, n) {
  var temp = arr[0];
  for (var i = 1; i < n; i++) {
    arr[i - 1] = arr[i];
  }
  arr[n - 1] = temp;
}

var arr = [1, 2, 3, 4, 5];
var n = 5;

console.log("Before Rotation");

for (var i = 0; i < n; i++) {
  console.log(arr[i] + " ");
}


lRotateOne(arr, n);

console.log("After Rotation");

for (var i = 0; i < n; i++) {
  console.log(arr[i] + " ");
}
```

&#x20;

**Output:**

```
Before Rotation
1 2 3 4 5 
After Rotation
2 3 4 5 1 

```
