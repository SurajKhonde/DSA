---
cover: >-
  https://images.unsplash.com/photo-1616628188502-413f2fe46e5e?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwxMHx8U29ydGluZ3xlbnwwfHx8fDE3MDcyMjM1MjJ8MA&ixlib=rb-4.0.3&q=85
coverY: 0
---

# Sorting

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

### **What is a stable sorting algorithm?**&#x20;

> A sorting algorithm is said to be stable if two objects with equal keys appear in the same order in sorted output as they appear in the input data set

Formally stability may be defined as, how the algorithm treats equal elements. Let **A\[]** be an array, and let **'<'** be a strict weak ordering on the elements of A\[].  A sorting algorithm is stable if: �<�����\[�]≡�\[�]��������(�)<�(�)where �is the sorting permutation ( sorting moves �\[�]to position �(�)) .

Informally, stability means that equivalent elements retain their relative positions, after sorting.

<figure><img src="https://media.geeksforgeeks.org/wp-content/uploads/20220825145858/del.png" alt="Example of stable sort"><figcaption><p>Example of stable sort</p></figcaption></figure>

### **Do we care for simple arrays like the array of integers?**&#x20;

When equal elements are indistinguishable, such as with integers, or more generally, any data where the entire element is the key, stability is not an issue. Stability is also not an issue if all keys are different.

### Where stable sorting algorithms are useful?

&#x20;Consider the following dataset of Student Names and their respective class sections.

&#x20;(����,�)(�����,�)(���,�)(����,�)(�����,�)

If we sort this data according to name only, then it is highly unlikely that the resulting dataset will be grouped according to sections as well.&#x20;

(�����,�)(�����,�)(����,�)(����,�)(���,�)

So we might have to sort again to obtain the list of students section-wise too. But in doing so, if the sorting algorithm is not stable, we might get a result like this:

(�����,�)(����,�)(���,�)(����,�)(�����,�)

The dataset is now sorted according to sections, but not according to names. In the name-sorted dataset, the tuple (Alice, B) was before (Eric, B) , but since the sorting algorithm is not stable, the relative order is lost. If on the other hand, we used a stable sorting algorithm, the result would be:

(�����,�)(����,�)(���,�)(�����,�)(����,�)

Here the relative order between different tuples is maintained. It may be the case that the relative order is maintained in an Unstable Sort but that is highly unlikely.

### **Which sorting algorithms are stable?**&#x20;

Some Sorting Algorithms are stable by nature, such as [Bubble Sort](https://www.geeksforgeeks.org/bubble-sort/), [Insertion Sort](https://www.geeksforgeeks.org/insertion-sort/), [Merge Sort](https://www.geeksforgeeks.org/merge-sort/), [Count Sort,](https://www.geeksforgeeks.org/counting-sort/) etc. Comparison-based stable sorts such as Merge Sort and Insertion Sort maintain stability by ensuring that- Element �\[�]comes before �\[�]if and only if �\[�]<�\[�], here i, j are indices, and �<�. The relative order is preserved![if A\[i\]\equiv A\[j\]](https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-0e0a7d4effb5635dcf90e9fb593eae45\_l3.svg)i.e.![A\[i\]](https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-4aaff26b720cb0edd0e2c823272f04f4\_l3.svg)comes before![A\[j\]](https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-bc58c90c6b04b4eeb97e44b1e6fef88d\_l3.svg).&#x20;

Other non-comparison-based sorts such as [Counting Sort](https://www.geeksforgeeks.org/counting-sort/) maintain stability by ensuring that the Sorted Array is filled in reverse order so that elements with equivalent keys have the same relative position. Some sorts such as [Radix Sort](https://www.geeksforgeeks.org/radix-sort/) depend on another sort, with the only requirement that the other sort should be stable.

### **Which sorting algorithms are unstable?**&#x20;

[Quick Sort](https://www.geeksforgeeks.org/quick-sort/), [Heap Sort](https://www.geeksforgeeks.org/heap-sort/) etc., can be made stable by also taking the position of the elements into consideration. This change may be done in a way that does not compromise a lot on the performance and takes some extra space, possibly �(�).

### **Can we make any sorting algorithm stable?**&#x20;

Any given sorting algorithm which is not stable can be modified to be stable. There can be algorithm-specific ways to make it stable, but in general, any comparison-based sorting algorithm which is not stable by nature can be modified to be stable by changing the key comparison operation so that the comparison of two keys considers position as a factor for objects with equal keys.
