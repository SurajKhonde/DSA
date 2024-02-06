---
cover: >-
  https://images.unsplash.com/photo-1616628188502-413f2fe46e5e?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwxMHx8U29ydGluZ3xlbnwwfHx8fDE3MDcyMjM1MjJ8MA&ixlib=rb-4.0.3&q=85
coverY: 0
---

# Sorting Array

<mark style="color:red;">**Introduction to Sorting**</mark>

**Sorting** any sequence means to arrange the elements of that sequence according to some specific criterion.\
\
For Example, the array arr\[] = {5, 4, 2, 1, 3} after _sorting in increasing order_ will be: arr\[] = {1, 2, 3, 4, 5}. The same array after _sorting in descending order_ will be: arr\[] = {5, 4, 3, 2, 1}.\
\
**In-Place Sorting**: An in-place sorting algorithm uses constant extra space for producing the output (modifies the given array only). It sorts the list only by modifying the order of the elements within the list. \
\
In this tutorial, we will see three of such in-place sorting algorithms, namely:\
&#x20;

* Insertion Sort
* Selection Sort
* Bubble Sort

\
\
&#x20;

#### Insertion Sort

\
Insertion Sort is an In-Place sorting algorithm. This algorithm works in a similar way of sorting a deck of playing cards. \
\
The idea is to start iterating from the second element of array till last element and for every element insert at its correct position in the subarray before it. \
\
In the below image you can see, how the array \[4, 3, 2, 10, 12, 1, 5, 6] is being sorted in increasing order following the insertion sort algorithm.

**Algorithm**:\
&#x20;

```
Step 1: If the current element is 1st element of array, 
        it is already sorted.
Step 2: Pick next element
Step 3: Compare the current element will all elements 
        in the sorted sub-array before it.
Step 4: Shift all of the elements in the sub-array before 
        the current element which are greater than the current 
        element by one place and insert the current element 
        at the new empty space.
Step 5: Repeat step 2-3 until the entire array is sorted.
```

\
\
**Another Example**: \
arr\[] = {**12**, 11, 13, 5, 6}\
\
Let us loop for i = 1 (second element of the array) to 4 (Size of input array - 1).\
&#x20;

* _i = 1_, Since 11 is smaller than 12, move 12 and insert 11 before 12. **11, 12,** 13, 5, 6
* _i = 2_, 13 will remain at its position as all elements in A\[0..I-1] are smaller than 13 **11, 12, 13,** 5, 6
* _i = 3_, 5 will move to the beginning and all other elements from 11 to 13 will move one position ahead of their current position. **5, 11, 12, 13,** 6
* _i = 4_, 6 will move to position after 5, and elements from 11 to 13 will move one position ahead of their current position. **5, 6, 11, 12, 13**\
  \
  &#x20;

#### Bubble Sort

\
Bubble Sort is also an in-place sorting algorithm. This is the simplest sorting algorithm and it works on the principle that:\
&#x20;

> \
> In one iteration if we swap all adjacent elements of an array such that after swap the first element is less than the second element then at the end of the iteration, the first element of the array will be the minimum element.\
> &#x20;

\
\
Bubble-Sort algorithm simply repeats the above steps N-1 times, where N is the size of the array.\
\
**Example:** Consider the array, arr\[] = {5, 1, 4, 2, 8}.\
&#x20;

* **First Pass:** ( **5** **1** 4 2 8 ) --> ( **1** **5** 4 2 8 ), Here, algorithm compares the first two elements, and swaps since 5 > 1. ( 1 **5** **4** 2 8 ) -->  ( 1 **4** **5** 2 8 ), Swap since 5 > 4 ( 1 4 **5** **2** 8 ) -->  ( 1 4 **2** **5** 8 ), Swap since 5 > 2 ( 1 4 2 **5** **8** ) --> ( 1 4 2 **5** **8** ), Now, since these elements are already in order (8 > 5), algorithm does not swap them.
* **Second Pass:** ( **1** **4** 2 5 8 ) --> ( **1** **4** 2 5 8 ) ( 1 **4** **2** 5 8 ) --> ( 1 **2** **4** 5 8 ), Swap since 4 > 2 ( 1 2 **4** **5** 8 ) --> ( 1 2 **4** **5** 8 ) ( 1 2 4 **5** **8** ) -->  ( 1 2 4 **5** **8** ) Now, the array is already sorted, but our algorithm does not know if it is completed. The algorithm needs one **whole** pass without **any** swap to know it is sorted.
* **Third Pass:** ( **1** **2** 4 5 8 ) --> ( **1** **2** 4 5 8 ) ( 1 **2** **4** 5 8 ) --> ( 1 **2** **4** 5 8 ) ( 1 2 **4** **5** 8 ) --> ( 1 2 **4** **5** 8 ) ( 1 2 4 **5** **8** ) --> ( 1 2 4 **5** **8** )

#### Selection Sort

\
The selection sort algorithm sorts an array by repeatedly finding the minimum element (considering ascending order) from unsorted part and putting it at the beginning. The algorithm maintains two subarrays in a given array.\
&#x20;

1. The subarray which is already sorted.
2. Remaining subarray which is unsorted.

\
\
In every iteration of selection sort, the minimum element (considering ascending order) from the unsorted subarray is picked and moved to the sorted subarray. \
\
Following example explains the above steps:\
&#x20;

<pre><code>arr[] = 64 25 12 22 11.

// Find the minimum element in arr[0...4]
// and place it at beginning
<strong>11 25 12 22 64
</strong>
// Find the minimum element in arr[1...4]
// and place it at beginning of arr[1...4]
<strong>11 12 25 22 64
</strong>
// Find the minimum element in arr[2...4]
// and place it at beginning of arr[2...4]
<strong>11 12 22 25 64
</strong>
// Find the minimum element in arr[3...4]
// and place it at beginning of arr[3...4]
<strong>11 12 22 25 64
</strong></code></pre>

Stability in Sorting Algorithm

***

Stability is mainly essential when we have key-value pairs with duplicate keys possible (like people's names as keys and their details as values). And we wish to sort these objects by keys.

<mark style="color:red;">**Quicksort**</mark><mark style="color:red;">:</mark> Quicksort is generally considered one of the fastest sorting algorithms for most practical data sets. It has an average-case time complexity of O(n log n) and performs well on average and best-case scenarios. However, in the worst-case scenario (e.g., if the pivot selection is poor), it can degrade to O(n^2).

###

```javascript
function quickSort(arr) {
    if (arr.length <= 1) {
        return arr;
    }

    const pivot = arr[Math.floor(arr.length / 2)]; // Choose the pivot element
    const left = [];
    const right = [];

    for (let i = 0; i < arr.length; i++) {
        if (i === Math.floor(arr.length / 2)) {
            continue; // Skip pivot element
        }
        if (arr[i] < pivot) {
            left.push(arr[i]); // Elements smaller than pivot go to the left
        } else {
            right.push(arr[i]); // Elements greater than pivot go to the right
        }
    }

    return [...quickSort(left), pivot, ...quickSort(right)]; // Recursively sort left and right parts
}

// Example usage:
let array = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5];
console.log("Original array:", array);
console.log("Sorted array:", quickSort(array));

```

<mark style="color:red;">**Mergesort**</mark> is another efficient sorting algorithm with a guaranteed <mark style="color:purple;">**worst-case time complexity of O(n log n).**</mark> It is a stable sorting algorithm and <mark style="color:blue;">works well for large data sets, but it requires additional space proportional to the size of the input array.</mark>



```javascript
function quickSort(arr) {
    if (arr.length <= 1) {
        return arr;
    }

    const pivot = arr[Math.floor(arr.length / 2)]; // Choose the pivot element
    const left = [];
    const right = [];

    for (let i = 0; i < arr.length; i++) {
        if (i === Math.floor(arr.length / 2)) {
            continue; // Skip pivot element
        }
        if (arr[i] < pivot) {
            left.push(arr[i]); // Elements smaller than pivot go to the left
        } else {
            right.push(arr[i]); // Elements greater than pivot go to the right
        }
    }

    return [...quickSort(left), pivot, ...quickSort(right)]; // Recursively sort left and right parts
}

// Example usage:
let array = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5];
console.log("Original array:", array);
console.log("Sorted array:", quickSort(array));

```

<mark style="color:red;">**min-heap and max-heap**</mark>

You can find the kth largest and kth smallest numbers in an array using various approaches, such as sorting the array or using data structures like heaps. Here, I'll provide two different methods: one using sorting and another using a min-heap and max-heap.



```javascript
function findKthLargestAndSmallest(array, k) {
    if (k < 1 || k > array.length) {
        return "Invalid value of k";
    }

    const sortedArray = array.slice().sort((a, b) => b - a); // Sort the array in descending order
    const kthLargest = sortedArray[k - 1];
    const kthSmallest = sortedArray[array.length - k];
    return { kthLargest, kthSmallest };
}

// Example usage:
let array = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5];
let k = 3;
console.log(`Kth Largest and Kth Smallest:`, findKthLargestAndSmallest(array, k));

```

You can sort an array of 0s, 1s, and 2s, also known as a Dutch National Flag problem, using the **Dutch National Flag Algorithm**. This algorithm sorts the array in a single pass, without using any additional space. Here's how you can implement it in JavaScript



```javascript
function sort012(arr) {
    let low = 0;
    let mid = 0;
    let high = arr.length - 1;

    while (mid <= high) {
        switch (arr[mid]) {
            case 0:
                [arr[low], arr[mid]] = [arr[mid], arr[low]];
                low++;
                mid++;
                break;
            case 1:
                mid++;
                break;
            case 2:
                [arr[mid], arr[high]] = [arr[high], arr[mid]];
                high--;
                break;
        }
    }
}

// Example usage:
let array = [0, 1, 2, 1, 0, 2, 1, 0];
console.log("Original array:", array);
sort012(array);
console.log("Sorted array:", array);

```

In this implementation:

* We maintain three pointers: `low`, `mid`, and `high`.
* `low` points to the next position where a 0 should be placed.
* `mid` is used to iterate through the array.
* `high` points to the next position where a 2 should be placed.
* We iterate through the array using the `mid` pointer.
* If `arr[mid]` is 0, we swap it with `arr[low]` and increment both `low` and `mid`.
* If `arr[mid]` is 1, we simply move to the next element by incrementing `mid`.
* If `arr[mid]` is 2, we swap it with `arr[high]` and decrement `high`. We don't increment `mid` in this case because we need to recheck the value at `arr[mid]` after the swap, as the swapped value may be 0 or 1.
* By the end of the iteration, the array will be sorted with 0s, 1s, and 2s grouped together.
