# Merge Sort

**Merge Sort** is a [Divide and Conquer](https://www.geeksforgeeks.org/divide-and-conquer-introduction/) algorithm. It divides the input array in two halves, calls itself for the two halves and then merges the two sorted halves. **The merge() function** is used for merging two halves. The merge(arr, l, m, r) is key process that assumes that arr\[l..m] and arr\[m+1..r] are sorted and merges the two sorted sub-arrays into one in a sorted manner. See following implementation for details:\


<pre><code><strong>MergeSort(arr[], l,  r)
</strong>If r > l
<strong>     1. Find the middle point to divide the array into two halves:  
</strong>             middle m = (l+r)/2
<strong>     2. Call mergeSort for first half:   
</strong>             Call mergeSort(arr, l, m)
<strong>     3. Call mergeSort for second half:
</strong>             Call mergeSort(arr, m+1, r)
<strong>     4. Merge the two halves sorted in step 2 and 3:
</strong>             Call merge(arr, l, m, r)
</code></pre>

The following diagram from [wikipedia](http://en.wikipedia.org/wiki/File:Merge\_sort\_algorithm\_diagram.svg) shows the complete merge sort process for an example array {38, 27, 43, 3, 9, 82, 10}. If we take a closer look at the diagram, we can see that the array is recursively divided in two halves till the size becomes 1. Once the size becomes 1, the merge processes comes into action and starts merging arrays back till the complete array is merged.

<figure><img src="https://media.geeksforgeeks.org/wp-content/cdn-uploads/Merge-Sort-Tutorial.png" alt=""><figcaption></figcaption></figure>

```javascript
function merge(a, b, m, n){
    let c = [];
    let i = 0, j = 0, k = 0;
    while(i<m && j<n){
        if(a[i]<b[j]) {
            c[k] = a[i];
            k++; i++;
        }
        else {
            c[k] = b[j];
            k++; j++;
        }
    }
    while(i<m) {
        c[k] = a[i];
        k++; i++;
    }
        
    while(j<n) {
        c[k] = b[j];
        k++; j++;
           }
    return c;
}

let a = [10,15,20,40];
let b = [5,6,6,10,15];

let m=a.length;
let n=b.length;
let c = merge(a,b,m,n);
console.log(c);
```

**Merge two Sorted Arrays**

Given two sorted arrays, the task is to merge them in a sorted manner.\
**Examples:**&#x20;

> _**Input**: arr1\[] = { 1, 3, 4, 5}, arr2\[] = {2, 4, 6, 8}_ \
> _**Output**: arr3\[] = {1, 2, 3, 4, 4, 5, 6, 8}_
>
> _**Input**: arr1\[] = { 5, 8, 9}, arr2\[] = {4, 7, 8}_ \
> _**Output**: arr3\[] = {4, 5, 7, 8, 8, 9}_&#x20;

**Method 1: (O(n1 \* n2) Time and O(n1+n2) Extra Space)**&#x20;

1. Create an array arr3\[] of size n1 + n2.
2. Copy all n1 elements of arr1\[] to arr3\[]
3. Traverse arr2\[] and one by one insert elements (like [insertion sort](https://www.geeksforgeeks.org/insertion-sort/)) of arr3\[] to arr1\[]. This step take O(n1 \* n2) time.

We have discussed implementation of above method in [Merge two sorted arrays with O(1) extra space](https://www.geeksforgeeks.org/merge-two-sorted-arrays-o1-extra-space/)\
**Method 2: (O(n1 + n2) Time and O(n1 + n2) Extra Space)** \
The idea is to use Merge function of [Merge sort](https://www.geeksforgeeks.org/merge-sort/).&#x20;

1. Create an array arr3\[] of size n1 + n2.
2. Simultaneously traverse arr1\[] and arr2\[].&#x20;
   * Pick smaller of current elements in arr1\[] and arr2\[], copy this smaller element to next position in arr3\[] and move ahead in arr3\[] and the array whose element is picked.
3. If there are remaining elements in arr1\[] or arr2\[], copy them also in arr3\[].

Below image is a dry run of the above approach:&#x20;

<figure><img src="https://media.geeksforgeeks.org/wp-content/uploads/20190708230512/editedMerge-two-sorted-arrays1.png" alt=""><figcaption></figcaption></figure>

```javascript
function merge(a, b, m, n){
    let c = [];
    let i = 0, j = 0, k = 0;
    while(i<m && j<n){
        if(a[i]<b[j]) {
            c[k] = a[i];
            k++; i++;
        }
        else {
            c[k] = b[j];
            k++; j++;
        }
    }
    while(i<m) {
        c[k] = a[i];
        k++; i++;
    }
        
    while(j<n) {
        c[k] = b[j];
        k++; j++;
          }
    return c;
}

let a = [10,15,20,40];
let b = [5,6,6,10,15];

let m=a.length;
let n=b.length;
let c = merge(a,b,m,n);
console.log(c);
```
