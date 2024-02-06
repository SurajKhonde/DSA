# Binary Search

Binary Search (Iterative)

***

&#x20;**Problem:** Given a sorted array **arr\[]** of **n** elements, write a function to search a given element **x** in **arr\[]** and return the index of x in the array. Consider array is 0 base index.

**Examples:**&#x20;

> _**Input:** arr\[] = {10, 20, 30, 50, 60, 80, 110, 130, 140, 170}, x = 110_\
> _**Output:** 6_\
> _**Explanation:** Element x is present at index 6._&#x20;
>
> _**Input:** arr\[] = {10, 20, 30, 40, 60, 110, 120, 130, 170}, x = 175_\
> _**Output:** -1_\
> _**Explanation:** Element x is not present in arr\[]._

**Linear Search Approach**: A simple approach is to do a [**linear search**](https://www.geeksforgeeks.org/linear-search/)**.** The time complexity of the Linear search is O(n). Another approach to perform the same task is using _Binary Search_. &#x20;

**Binary Search Approach:**&#x20;

> _**Binary Search** is a_ [_searching algorithm_](https://www.geeksforgeeks.org/searching-algorithms/) _used in a sorted array by **repeatedly dividing the search interval in half**. The idea of binary search is to use the information that the array is sorted and reduce the time complexity to O(Log n)._

**Binary Search Algorithm:** The basic steps to perform Binary Search are:

* Sort the array in ascending order.
* Set the low index to the first element of the array and the high index to the last element.
* Set the middle index to the average of the low and high indices.
* If the element at the middle index is the target element, return the middle index.
* If the target element is less than the element at the middle index, set the high index to the middle index – 1.
* If the target element is greater than the element at the middle index, set the low index to the middle index + 1.
* Repeat steps 3-6 until the element is found or it is clear that the element is not present in the array.

<mark style="color:red;">**Step-by-step Binary Search Algorithm**</mark>**:** We basically ignore half of the elements just after one comparison.

1. Compare x with the middle element.
2. If x matches with the middle element, we return the mid index.
3. Else If x is greater than the mid element, then x can only lie in the right half subarray after the mid element. So we recur for the right half.
4. Else (x is smaller) recur for the left half.

```javascript
// Program to implement iterative Binary Search


// A iterative binary search function. It returns
// location of x in given array arr[l..r] is present,
// otherwise -1

function binarySearch(arr, x)
{
	let l = 0;
	let r = arr.length - 1;
	let mid;
	while (r >= l) {
		mid = l + Math.floor((r - l) / 2);

		// If the element is present at the middle
		// itself
		if (arr[mid] == x)
			return mid;

		// If element is smaller than mid, then
		// it can only be present in left subarray
		if (arr[mid] > x)
			r = mid - 1;
			
		// Else the element can only be present
		// in right subarray
		else
			l = mid + 1;
	}

	// We reach here when element is not
	// present in array
	return -1;
}

	arr =new Array(2, 3, 4, 10, 40);
	x = 10;
	n = arr.length;
	result = binarySearch(arr, x);
	
(result == -1) ? console.log("Element is not present in array")
			: console.log ("Element is present at index " + result);
```

```
Element is present at index 3
```

**Time Complexity:** O(log n)\
**Auxiliary Space:** O(1)\


**Binary Search (Recursive)**

**Problem:** Given a sorted array **arr\[]** of **n** elements, write a function to search a given element **x** in **arr\[]** and return the index of x in the array.

&#x20;                Consider array is 0 base index.

**Examples:**&#x20;

> _**Input:** arr\[] = {10, 20, 30, 50, 60, 80, 110, 130, 140, 170}, x = 110_\
> _**Output:** 6_\
> _**Explanation:** Element x is present at index 6._&#x20;
>
> _**Input:** arr\[] = {10, 20, 30, 40, 60, 110, 120, 130, 170}, x = 175_\
> _**Output:** -1_\
> _**Explanation:** Element x is not present in arr\[]._

**Binary Search Approach:**&#x20;

> _**Binary Search** is a_ [_searching algorithm_](https://www.geeksforgeeks.org/searching-algorithms/) _used in a sorted array by **repeatedly dividing the search interval in half**. The idea of binary search is to use the information that the array is sorted and reduce the time complexity to O(Log n)._&#x20;

**Binary Search Algorithm:** The basic steps to perform Binary Search are:

* Begin with the mid element of the whole array as a search key.
* If the value of the search key is equal to the item then return an index of the search key.
* Or if the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half.
* Otherwise, narrow it to the upper half.
* Repeatedly check from the second point until the value is found or the interval is empty.

Recursive Method (The recursive method follows the divide and conquer approach)

```
    binarySearch(arr, x, low, high)
           if low > high
               return False 
   
           else
               mid = (low + high) / 2 
                   if x == arr[mid]
                   return mid
       
               else if x > arr[mid]        // x is on the right side
                   return binarySearch(arr, x, mid + 1, high)
               
               else                        // x is on the left side
                   return binarySearch(arr, x, low, mid - 1) 
```

**Step-by-step Binary Search Algorithm:** We basically ignore half of the elements just after one comparison.

1. Compare x with the middle element.
2. If x matches with the middle element, we return the mid index.
3. Else If x is greater than the mid element, then x can only lie in the right half subarray after the mid element. So we recur for the right half.
4. Else (x is smaller) recur for the left half.

**Recursive implementation of Binary Search**:

Javascript

```javascript
// JavaScript implementation of recursive Binary Search

function binarySearch(arr, l, r, x) {
  if (r >= l) {
    let mid = Math.floor(l + (r - l) / 2);

    // If the element is present at the middle
    if (arr[mid] === x) return mid;

    // If element is smaller than mid, then
    // it can only be present in left subarray
    if (arr[mid] > x) return binarySearch(arr, l, mid - 1, x);

    // Else the element can only be present
    // in right subarray
    return binarySearch(arr, mid + 1, r, x);
  }

  // We reach here when element is not
  // present in array
  return -1;
}

let arr = [2, 3, 4, 10, 40];
let x = 10;
let n = arr.length;
let result = binarySearch(arr, 0, n - 1, x);

if (result === -1) {
  console.log("Element is not present in array");
} else {
  console.log("Element is present at index " + result);
}
```

&#x20;

**Output**

```
Element is present at index 3
```

**Time Complexity:** O(log n)\
**Auxiliary Space:** O(log n)

&#x20;Index of first occurrence in sorted

***

### An e**fficient approach** using binary search:&#x20;

**1. For the first occurrence of a number**&#x20;

> _a) If (high >= low)_\
> _b) Calculate  mid = low + (high – low)/2;_\
> _c) If ((mid == 0 || x > arr\[mid-1]) && arr\[mid] == x)_\
> &#x20;       _return mid;_\
> _d) Else if (x > arr\[mid])_\
> &#x20;      _return first(arr, (mid + 1), high, x, n);_\
> _e) Else_\
> &#x20;      _return first(arr, low, (mid -1), x, n);_\
> _f) Otherwise return -1;_

**2. For the last occurrence of a number**&#x20;

> _a) if (high >= low)_\
> _b) calculate mid = low + (high – low)/2;_\
> _c)if( ( mid == n-1 || x < arr\[mid+1]) && arr\[mid] == x )_\
> &#x20;       _return mid;_\
> _d) else if(x < arr\[mid])_\
> &#x20;      _return last(arr, low, (mid -1), x, n);_\
> _e) else_\
> &#x20;     _return last(arr, (mid + 1), high, x, n);_      \
> _f) otherwise return -1;_

Below is the implementation of the above approach:

Javascript

```javascript
function first(arr, x, n) {
  let low = 0, high = n - 1, res = -1;
  while (low <= high) {
    let mid = Math.floor((low + high) / 2);
    if (arr[mid] > x) {
      high = mid - 1;
    } else if (arr[mid] < x) {
      low = mid + 1;
    } else {
      res = mid;
      high = mid - 1;
    }
  }
  return res;
}

let arr = [1, 2, 2, 2, 2, 3, 4, 7, 8, 8];
let n = arr.length;
let x = 8;
console.log("First Occurrence = " + first(arr, x, n));
```

&#x20;

**Output**

```
First Occurrence = 8    
```

**Time Complexity:** O(log n) \
**Auxiliary Space:** O(1)

### **An Iterative Implementation of Binary Search Solution :**

> 1. _For the **first occurrence**, we will first find the index of the number and then search again in the left subarray as long as we are finding the number._\
>    &#x20;
> 2. _For the **last occurrence**, we will first find the index of the number and then search again in the right subarray as long as we are finding the number_

**First occurrence:**&#x20;

* Do while low <= high:
  * First, find the mid element
  * Check if the arr\[mid] > x then the first element will occur on the left side of mid. So, bring the high pointer to mid – 1
  * Check if the arr\[mid] < x then the first element will occur on the right side of mid. So, bring the low pointer to mid + 1
  * If arr\[mid] == x then this may be the first element. So, update the result to mid and move the high pointer to mid – 1.
* Return the result.

**Last occurrence:**&#x20;

* Do while low <= high:
  * First, find the mid element
  * Check if the arr\[mid] > x then the last element will occur on the left side of mid. So, bring the low pointer to mid – 1
  * Check if the arr\[mid] < x then the last element will occur on the right side of mid. So, bring the low pointer to mid + 1
  * If arr\[mid] == x then this may be the last element. So, update the result to mid and move the low pointer to mid + 1.
* Finally, Return the result.

Below is the implementation of the above approach:

Javascript

```javascript
function first(arr, x, n) {
  let low = 0;
  let high = n - 1;
  let res = -1;
  while (low <= high) {
    // Normal Binary Search Logic
    let mid = Math.floor((low + high) / 2);
    if (arr[mid] > x) {
      high = mid - 1;
    } else if (arr[mid] < x) {
      low = mid + 1;
    } else {
      res = mid;
      high = mid - 1;
    }
  }
  return res;
}

let arr = [1, 2, 2, 2, 2, 3, 4, 7, 8, 8];
let n = arr.length;

let x = 8;
console.log(`First Occurrence = ${first(arr, x, n)}`);
```

&#x20;

**Output**

```
First Occurrence = 8
```

**Time Complexity**: O(log n) \
**Auxiliary Space:** O(1)&#x20;

Index of last occurrence in sorted

***

### An e**fficient approach** using binary search:&#x20;

**1. For the last occurrence of a number**&#x20;

> _a) if (high >= low)_\
> _b) calculate mid = low + (high – low)/2;_\
> _c)if( ( mid == n-1 || x < arr\[mid+1]) && arr\[mid] == x )_\
> &#x20;       _return mid;_\
> _d) else if(x < arr\[mid])_\
> &#x20;      _return last(arr, low, (mid -1), x, n);_\
> _e) else_\
> &#x20;     _return last(arr, (mid + 1), high, x, n);_      \
> _f) otherwise return -1;_

Below is the implementation of the above approach:

Javascript

```javascript
const last = (arr, low, high, x, n) => {
  if (high >= low) {
    const mid = low + Math.floor((high - low) / 2);
    if ((mid === n - 1 || x < arr[mid + 1]) && arr[mid] === x) {
      return mid;
    } else if (x < arr[mid]) {
      return last(arr, low, mid - 1, x, n);
    } else {
      return last(arr, mid + 1, high, x, n);
    }
  }
  return -1;
};

const arr = [1, 2, 2, 2, 2, 3, 4, 7, 8, 8];
const n = arr.length;
const x = 8;
console.log("Last Occurrence = " + last(arr, 0, n - 1, x, n));
```

&#x20;

**Output**

```
  Last Occurrence = 9
```

**Time Complexity:** O(log n) \
**Auxiliary Space:** O(1)

### **An Iterative Implementation of Binary Search Solution :** &#x20;

> 1. _For the **last occurrence**, we will first find the index of the number and then search again in the right subarray as long as we are finding the number_

**Last occurrence:**&#x20;

* Do while low <= high:
  * First, find the mid element
  * Check if the arr\[mid] > x then the last element will occur on the left side of mid. So, bring the low pointer to mid – 1
  * Check if the arr\[mid] < x then the last element will occur on the right side of mid. So, bring the low pointer to mid + 1
  * If arr\[mid] == x then this may be the last element. So, update the result to mid and move the low pointer to mid + 1.
* Finally, Return the result.

Below is the implementation of the above approach:

Javascript

```javascript
const arr = [1, 2, 2, 2, 2, 3, 4, 7, 8, 8];
const n = arr.length;
const x = 8;

function last(arr, x, n) {
  let low = 0;
  let high = n - 1;
  let res = -1;
  while (low <= high) {
    const mid = Math.floor((low + high) / 2);
    if (arr[mid] > x) {
      high = mid - 1;
    } else if (arr[mid] < x) {
      low = mid + 1;
    } else {
      res = mid;
      low = mid + 1;
    }
  }
  return res;
}

console.log(`Last Occurrence = ${last(arr, x, n)}`);
```

&#x20;

**Output**

```
Last Occurrence = 9
```

**Time Complexity**: O(log n) \
**Auxiliary Space:** O(1)&#x20;

Count Occurrences in Sorted

***

Given a sorted array arr\[] and a number x, write a function that counts the occurrences of x in arr\[]. Expected time complexity is O(Logn)&#x20;

**Examples:**&#x20;

<pre><code><strong>  Input: arr[] = {1, 1, 2, 2, 2, 2, 3,},   x = 2
</strong><strong>  Output: 4 // x (or 2) occurs 4 times in arr[]
</strong>
<strong>  Input: arr[] = {1, 1, 2, 2, 2, 2, 3,},   x = 3
</strong><strong>  Output: 1 
</strong>
<strong>  Input: arr[] = {1, 1, 2, 2, 2, 2, 3,},   x = 1
</strong><strong>  Output: 2 
</strong>
<strong>  Input: arr[] = {1, 1, 2, 2, 2, 2, 3,},   x = 4
</strong><strong>  Output: -1 // 4 doesn't occur in arr[] 
</strong></code></pre>

**Method: Binary Search**

Javascript

```javascript
function firstOcc(arr, n, x) {
  let low = 0;
  let high = n - 1;

  while (low <= high) {
    let mid = Math.floor((low + high) / 2);

    if (x > arr[mid]) {
      low = mid + 1;
    } else if (x < arr[mid]) {
      high = mid - 1;
    } else {
      if (mid === 0 || arr[mid - 1] !== arr[mid]) {
        return mid;
      } else {
        high = mid - 1;
      }
    }
  }

  return -1;
}

function lastOcc(arr, n, x) {
  let low = 0;
  let high = n - 1;

  while (low <= high) {
    let mid = Math.floor((low + high) / 2);

    if (x > arr[mid]) {
      low = mid + 1;
    } else if (x < arr[mid]) {
      high = mid - 1;
    } else {
      if (mid === n - 1 || arr[mid + 1] !== arr[mid]) {
        return mid;
      } else {
        low = mid + 1;
      }
    }
  }

  return -1;
}

function countOcc(arr, n, x) {
  let first = firstOcc(arr, n, x);

  if (first === -1) {
    return 0;
  } else {
    return lastOcc(arr, n, x) - first + 1;
  }
}

let arr = [10, 20, 20, 20, 40, 40];
let n = 6;
let x = 20;

console.log(countOcc(arr, n, x));
```

&#x20;

**Output :**&#x20;

```
3
```

**Time Complexity :** O(Log n)

**Space Complexity:** O(1)

Square root

***

Given an integer **X**, find its square root. If **X** is not a perfect square, then return **floor(√x)**.

**Examples :**&#x20;

> _**Input:** x = 4_\
> _**Output:** 2_\
> _**Explanation:** The square root of 4 is 2._
>
> _**Input:** x = 11_\
> _**Output:** 3_\
> _**Explanation:**  The square root of 11 lies in between 3 and 4 so floor of the square root is 3._

**Naive Approach:** To find the floor of the square root, try with all-natural numbers starting from 1. Continue incrementing the number until the square of that number is greater than the given number.

Follow the steps below to implement the above idea

1. Create a variable (counter) _**i**_ and take care of some base cases, (i.e when the given number is 0 or 1).
2. Run a loop until _**i\*i <= n**_, where n is the given number. Increment i by 1.
3. The floor of the square root of the number is _i – 1_

Below is the implementation of the above approach:

Javascript

```javascript
function floorSqrt(x) {
  if (x === 0 || x === 1) {
    return x;
  }
  let i = 1, result = 1;
  while (result <= x) {
    i++;
    result = i * i;
  }
  return i - 1;
}

console.log(floorSqrt(11));
```

&#x20;

**Output**

```
3
```

**Complexity Analysis:**&#x20;

* **Time Complexity:** O(√X). Only one traversal of the solution is needed, so the time complexity is O(√X).
* **Auxiliary Space:** O(1).

### **Square root an integer using Binary search:**

> _The idea is to find the largest integer **i** whose square is less than or equal to the given number. The values of **i \* i** is monotonically increasing, so the problem can be solved using binary search._

**Below is the implementation of the above idea:**&#x20;

1. Base cases for the given problem are when the given number is **0** or **1**, then return **X**;
2. Create some variables, for storing the lower bound say _**l = 0,** and for upper bound_ _**r = X / 2** (i.e, The floor of the square root of x cannot be more than x/2 when x > 1)._
3. Run a loop until _**l <= r**_, the search space vanishes
4. Check if the square of mid **(**_**mid = (l + r)/2**_** )** is less than or equal to **X**, If yes then search for a larger value in the second half of the search space, i.e **l = mid + 1**, update **ans = mid**
5. Else if the square of mid is more than **X** then search for a smaller value in the first half of the search space, i.e **r = mid – 1**
6. Finally, Return the **ans**

Below is the implementation of the above approach:

Javascript

```javascript
function floorSqrt(x) {
  if (x === 0 || x === 1) {
    return x;
  }

  let start = 1;
  let end = x / 2;
  let ans;

  while (start <= end) {
    let mid = Math.floor((start + end) / 2);
    let sqr = mid * mid;

    if (sqr === x) {
      return mid;
    }

    if (sqr <= x) {
      start = mid + 1;
      ans = mid;
    } else {
      end = mid - 1;
    }
  }

  return ans;
}

console.log(floorSqrt(11));
```

&#x20;

**Output**

```
3
```

**Complexity Analysis:**&#x20;

* **Time Complexity:** O(log(X)).&#x20;
* **Auxiliary Space:** O(1)

Count 1s in a Sorted Binary Array

***

Given a binary array **arr\[]** of size **N,** which is sorted in **non-increasing order**, count the number of **1’s** in it.&#x20;

**Examples:**&#x20;

> _**Input:** arr\[] = {1, 1, 0, 0, 0, 0, 0}_\
> _**Output:** 2_
>
> _**Input:** arr\[] = {1, 1, 1, 1, 1, 1, 1}_\
> _**Output:** 7_
>
> _**Input:** arr\[] = {0, 0, 0, 0, 0, 0, 0}_\
> _**Output:** 0_

_**Method: Binary Search**_

Javascript

```javascript
function countOnes(arr, n) {
    let low = 0, high = n - 1;
    while (low <= high) {
        let mid = Math.floor((low + high) / 2);
        if (arr[mid] === 0) {
            low = mid + 1;
        } else {
            if (mid === 0 || arr[mid - 1] === 0) {
                return (n - mid);
            } else {
                high = mid - 1;
            }
        }
    }
    return 0;
}

let arr = [0, 0, 1, 1, 1, 1], n = 6;
console.log(countOnes(arr, n));
```

&#x20;

**Output**

```
4
```

**Time complexity:** O(Log(N))\
**Auxiliary Space:** O(1)

&#x20;\
\
