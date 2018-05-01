Write a function to check if any permutation of a string is a palindrome.

```Javascript
function myFunction(arg) {
    arg = arg.toLowerCase();
    let keeper = new Set();

    for (let i = 0; i < arg.length; i++) {
        let letter = arg[i];

        if (keeper.has(letter)) keeper.delete(letter);
        else {
            keeper.add(letter);
        }
    }
    return keeper.size <= 1;
}

console.log(myFunction('racecar'));
console.log(myFunction('palindrome'));
console.log(myFunction('CiViC'));
```