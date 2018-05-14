Create a BinarySearchTree

```Javascript
function Node(val) {
    this.value = val;
    this.left = null;
    this.right = null;
}

function BinarySearchTree() {
    this.root = null;
}

BinarySearchTree.prototype.insert = function(val) {
    if (!this.root) {
        this.root = new Node(val);
    } else {
        let currentNode = this.root;
        let newNode = new Node(val);

        while(currentNode) {
            if (val <= currentNode.value) {
                if (!currentNode.left) {
                    currentNode.left = newNode;
                    break;
                } else {
                    currentNode = currentNode.left;
                }
            } else {
                if (!currentNode.right) {
                    currentNode.right = newNode;
                    break;
                } else {
                    currentNode = currentNode.right;
                }
            }
        }
    }
}

let tree = new BinarySearchTree();
tree.insert(5);
tree.insert(3);
tree.insert(4);
tree.insert(6);
tree.insert(7);
tree.insert(8);
tree.insert(2);
```

Create an iterative function that checks to see if a value exists in your binary search tree
```Javascript
BinarySearchTree.prototype.contains = function (val) {
    let currentNode = this.root;

    while (currentNode) {
        if (currentNode.value === val) {
            return true;
        }
        if (val < currentNode.value) {
            if (currentNode.left) {
                currentNode = currentNode.left;
            } else {
                return false;
            }
        } else if (val > currentNode.value) {
            if (currentNode.right) {
                currentNode = currentNode.right;
            } else {
                return false;
            }
        }
    }
}
```

Create a recursive function that checks to see if a value exists in your binary search tree
```Javascript
BinarySearchTree.prototype.contains = function (val, current) {
    if (!current) {
        current = this.root;
    }
    if (val === current.value) {
        return true;
    } else {
        while (current) {
            if (val <= current.value && current.left) {
                return this.contains(val, current.left);
            } else if (val > current.value && current.right) {
                return this.contains(val, current.right);
            }
            return false;
        }
    }
}
console.log(tree.contains(2)); // true
console.log(tree.contains(500)); // false
console.log(tree.contains(8)); // true
console.log(tree.contains(7)); // true
console.log(tree.contains(100)); // false
```