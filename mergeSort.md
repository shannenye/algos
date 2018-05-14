Write a recursive merge sort function

```Javascript
function mergeSort(arr) {
    let middle = Math.floor(arr.length/2);
    let left = arr.slice(0, middle);
    let right = arr.slice(middle, arr.length);

    if (arr.length < 2) {
        return arr;
    } else {
        return merge(mergeSort(left), mergeSort(right));
    }
}

function merge(left, right) {
    let mergedArr = [];

    while (left.length && right.length) {
        if (left[0] <= right[0]) {
            mergedArr.push(left.shift());
        } else {
            mergedArr.push(right.shift());
        }
    }
    while (left.length) {
        mergedArr.push(left.shift());
    }
    while (right.length) {
        mergedArr.push(right.shift());
    }
    return mergedArr;
}

console.log(mergeSort([5,9,3,10,12,2,6,1,7,8]));
console.log(mergeSort([1]));
console.log(mergeSort([2,1]));
console.log(mergeSort([30,19,2,0,11,6,24]));
```
