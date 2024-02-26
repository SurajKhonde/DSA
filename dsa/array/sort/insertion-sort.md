# Insertion sort

**Insertion sort** is a simple sorting algorithm that works similar to the way you sort playing cards in your hands. The array is virtually split into a sorted and an unsorted part. Values from the unsorted part are picked and placed at the correct position in the sorted part.

#### **Characteristics of Insertion Sort:**

* This algorithm is one of the simplest algorithm with simple implementation
* Basically, Insertion sort is efficient for small data values
* Insertion sort is adaptive in nature, i.e. it is appropriate for data sets which are already partially sorted.

#### Working of Insertion Sort algorithm:

_Consider an example: arr\[]: {12, 11, 13, 5, 6}_

|    _12_    |    _11_    |    _13_    |    _5_    |    _6_    |
| ---------- | ---------- | ---------- | --------- | --------- |

_**First Pass:**_

* _Initially, the first two elements of the array are compared in insertion sort._

|    _**12**_    |    _**11**_    |    _13_    |    _5_    |    _6_    |
| -------------- | -------------- | ---------- | --------- | --------- |

* _Here, 12 is greater than 11 hence they are not in the ascending order and 12 is not at its correct position. Thus, swap 11 and 12._
* _So, for now 11 is stored in a sorted sub-array._

|    _**11**_    |    _**12**_    |    _13_    |    _5_    |    _6_    |
| -------------- | -------------- | ---------- | --------- | --------- |

_**Second Pass:**_

* &#x20;_Now, move to the next two elements and compare them_

|    _11_    |    _**12**_    |    _**13**_    |    _5_    |    _6_    |
| ---------- | -------------- | -------------- | --------- | --------- |

* _Here, 13 is greater than 12, thus both elements seems to be in ascending order, hence, no swapping will occur. 12 also stored in a sorted sub-array along with 11_

_**Third Pass:**_

* _Now, two elements are present in the sorted sub-array which are **11** and **12**_
* _Moving forward to the next two elements which are 13 and 5_

|    _11_    |    _12_    |    _**13**_    |    _**5**_    |    _6_    |
| ---------- | ---------- | -------------- | ------------- | --------- |

* _Both 5 and 13 are not present at their correct place so swap them_

|    _11_    |    _12_    |    _**5**_    |    _**13**_    |    _6_    |
| ---------- | ---------- | ------------- | -------------- | --------- |

* _Here, 13 is greater than 12, thus both elements seems to be in ascending order, hence, no swapping will occur. 12 also stored in a sorted sub-array along with 11_

_**Third Pass:**_

* _Now, two elements are present in the sorted sub-array which are **11** and **12**_
* _Moving forward to the next two elements which are 13 and 5_

|    _11_    |    _12_    |    _**13**_    |    _**5**_    |    _6_    |
| ---------- | ---------- | -------------- | ------------- | --------- |

* _Both 5 and 13 are not present at their correct place so swap them_

|    _11_    |    _12_    |    _**5**_    |    _**13**_    |    _6_    |
| ---------- | ---------- | ------------- | -------------- | --------- |

* _Now, the elements which are present in the sorted sub-array are **5, 11** and **12**_
* _Moving to the next two elements 13 and 6_

|    _5_    |    _11_    |    _12_    |    _**13**_    |    _**6**_    |
| --------- | ---------- | ---------- | -------------- | ------------- |

* _Clearly, they are not sorted, thus perform swap between both_

|    _5_    |    _11_    |    _12_    |    _**6**_    |    _**13**_    |
| --------- | ---------- | ---------- | ------------- | -------------- |

* _Now, 6 is smaller than 12, hence, swap again_

|    _5_    |    _11_    |    _**6**_    |    _**12**_    |    _13_    |
| --------- | ---------- | ------------- | -------------- | ---------- |

* _Here, also swapping makes 11 and 6 unsorted hence, swap again_

|    _5_    |    _**6**_    |    _**11**_    |    _12_    |    _13_    |
| --------- | ------------- | -------------- | ---------- | ---------- |

* _Finally, the array is completely sorted._

#### **Insertion Sort Algorithm**&#x20;

To sort an array of size N in ascending order:&#x20;

* Iterate from arr\[1] to arr\[N] over the array.&#x20;
* Compare the current element (key) to its predecessor.&#x20;
* If the key element is smaller than its predecessor, compare it to the elements before. Move the greater elements one position up to make space for the swapped elem

```javascript
function iSort(arr, n) {
    for(let i = 1; i < n; i++){
        let key = arr[i];
        let j=i-1;
        while(j >= 0 && arr[j] > key) {
            arr[j+1]=arr[j];
            j--;
        }
        arr[j+1] = key;
    }
    return arr;
}

let arr = [50,20,40,60,10,30];

let n=arr.length;
iSort(arr,n);

console.log(arr);
```
