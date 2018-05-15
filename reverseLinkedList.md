Write a function to create a Linked List

```Javascript
function Node(val) {
    this.value = val;
    this.next = null;
}

function LinkedList() {
    this.root = null;
}

LinkedList.prototype.insert = function(val) {
    if (!this.root) {
        this.root = new Node(val);
    } else {
        let currentNode = this.root;
        let newNode = new Node(val);

        while(currentNode) {
            if (!currentNode.next) {
                currentNode.next = newNode;
                break;
            } else {
                currentNode = currentNode.next;
            }
        }
    }
}

let l = new LinkedList();
l.insert(5); // 5
l.insert(1); // 5 => 1
l.insert(7); // 5 => 7
l.insert(4); // 5 => 7 => 4
l.insert(2); // 5 => 7 => 4 => 2
l.insert(6); // 5 => 7 => 4 => 2 => 6
```

Write a function to reverse the linked list

```Javascript
LinkedList.prototype.reverseList = function() {
    let currentNode = this.root;
    let previousNode = null;
    let nextNode = null;

    while(currentNode) {
        nextNode = currentNode.next;
        currentNode.next = previousNode;
        previousNode = currentNode;
        currentNode = nextNode;
    }
    return previousNode;
}

l.reverseList();
```