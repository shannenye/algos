Given an array, find the highest product of 3 numbers.

```Javascript
function highestProductOf3(arr) {
    let highest2 = arr[0] * arr[1];
    let highest3 = arr[0] * arr[1] * arr[2];
    let lowest2 = arr[0] * arr[1];
    let highestNum = Math.max(arr[0], arr[1]);
    let lowestNum = Math.min(arr[0], arr[1]);

    if (arr.length < 3) {
        throw new Error(`Doesn't have 3 elements!`);
    }
    for (let i = 2; i < arr.length; i++) {
        let current = arr[i];

        highest3 = Math.max(highest3, current * highest2, current * lowest2);
        highest2 = Math.max(highest2, current * highestNum, current * lowestNum);
        lowest2 = Math.min(lowest2, current * highestNum, current * lowestNum);
        highestNum = Math.max(highestNum, current);
        lowestNum = Math.min(lowestNum, current);
    }
    return highest3;
}

console.log(highestProductOf3([-5, -1, -3, -2])); // -6
console.log(highestProductOf3([6, 1, 3, 5, 7, 8, 2])); // 336
console.log(highestProductOf3([1,2])); // Error: Doesn't have 3 elements!
```