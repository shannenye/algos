Given an arr, return the highest sum of three numbers
(To find the array of 3 numbers, uncomment all the code inside the below function and return top3Nums instead of highest3)

```Javascript
function highestSum (arr) {
    let highestNum = Math.max(arr[0], arr[1]);
    let lowestNum = Math.min(arr[0], arr[1]);
    let highest2 = arr[0] + arr[1];
    let lowest2 = arr[0] + arr[1];
    let highest3 = arr[0] + arr[1] + arr[2];
    // let top3Nums = [];

    for (let i = 2; i < arr.length; i++) {
        let current = arr[i];


        highest3 = Math.max(highest3, current + highest2, current + lowest2);
        highest2 = Math.max(highest2, current + highestNum, current + lowestNum);
        lowestNum = Math.min(lowestNum, current + highestNum, current + lowestNum);
        highestNum = Math.max(highestNum, current);
        lowestNum = Math.min(lowestNum, current);
        // top3Nums = [highest3 - highest2, highest2 - highestNum, highestNum]
    }
    // return top3Nums;
    return highest3;
}

console.log(highestSum([10,11,1,2,3,4,12,5,6])); // 33
console.log(highestSum([1,2,13,4,5,6,3,14,19,0])); // 46
```