# Page 1

To reverse an array in <mark style="color:red;">**JavaScript**</mark>, you can use various methods. Below is one approach using a loop to reverse the array in-place.



```javascript
function reverseArray(arr) {
    let start = 0;
    let end = arr.length - 1;
    
    while (start < end) {
        // Swap elements at start and end indices
        let temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        
        // Move start pointer towards the end and end pointer towards the start
        start++;
        end--;
    }
    
    return arr;
}

// Example usage:
let arr = [1, 2, 3, 4, 5];
console.log(reverseArray(arr)); // Output: [5, 4, 3, 2, 1]

```

time complexity of O(n/2)

<mark style="color:red;">**minimum and maximum**</mark>



```javascript
function findMinMax(arr) {
    if (arr.length === 0) {
        return "Array is empty";
    }

    let min = arr[0];
    let max = arr[0];

    for (let i = 1; i < arr.length; i++) {
        if (arr[i] < min) {
            min = arr[i];
        }
        if (arr[i] > max) {
            max = arr[i];
        }
    }

    return { min, max };
}

// Example usage:
let array = [3, 8, 2, 5, 10, 1];
let result = findMinMax(array);
console.log("Minimum:", result.min); // Output: Minimum: 1
console.log("Maximum:", result.max); // Output: Maximum: 10
```

A <mark style="color:red;">peak element</mark> in an array is an element that is greater than or equal to its neighbors. If an element is the first or last element, it is only compared to one neighbor. We can find a peak element in an array using various methods, such as linear search, binary search, or <mark style="color:red;">**divide-and-conquer algorithms.**</mark>



```javascript
function findPeakElement(arr) {
    for (let i = 0; i < arr.length; i++) {
        // Check if the current element is greater than or equal to its neighbors
        if ((i === 0 || arr[i] >= arr[i - 1]) && (i === arr.length - 1 || arr[i] >= arr[i + 1])) {
            return arr[i];
        }
    }
    return null; // No peak element found
}

// Example usage:
let array = [1, 3, 20, 4, 1, 0];
console.log("Peak Element:", findPeakElement(array)); // Output: Peak Element: 20

```
