# Binary Search Tree (BST) Data Structure in JavaScript 🚀  

A simple implementation of the **Binary Search Tree (BST)** data structure in JavaScript. This repository demonstrates how to create a binary search tree class with essential methods and explains its functionality with practical examples.  

---

## What is a Binary Search Tree?  
A **Binary Search Tree (BST)** is a tree data structure where each node has at most two children, referred to as the left and right children. The left child’s value is less than the parent node’s value, and the right child’s value is greater than the parent node’s value. This property allows for efficient searching, insertion, and deletion operations.  

---

## Features  
- **Insert**: Add a new node to the BST.  
- **Delete**: Remove a node from the BST.  
- **Search**: Find a node in the BST.  
- **Traverse**: Visit each node in the tree (in-order, pre-order, post-order).  
- **Size**: Get the number of nodes in the tree.  

---

## Code Implementation  

Here’s the JavaScript implementation of the binary search tree:  

```javascript
class Node {
    constructor(value) {
        this.value = value; // Value of the node
        this.left = null; // Left child
        this.right = null; // Right child
    }
}

class BinarySearchTree {
    constructor() {
        this.root = null; // Root of the tree
        this.size = 0; // Number of nodes in the tree
    }

    // Insert a value into the BST
    insert(value) {
        const newNode = new Node(value);
        if (this.root === null) {
            this.root = newNode;
        } else {
            this.insertNode(this.root, newNode);
        }
        this.size++;
    }

    // Helper function to insert a node
    insertNode(node, newNode) {
        if (newNode.value < node.value) {
            if (node.left === null) {
                node.left = newNode;
            } else {
                this.insertNode(node.left, newNode);
            }
        } else {
            if (node.right === null) {
                node.right = newNode;
            } else {
                this.insertNode(node.right, newNode);
            }
        }
    }

    // Search for a node by its value
    search(value) {
        return this.searchNode(this.root, value);
    }

    // Helper function to search for a node
    searchNode(node, value) {
        if (node === null) {
            return null;
        }
        if (value < node.value) {
            return this.searchNode(node.left, value);
        } else if (value > node.value) {
            return this.searchNode(node.right, value);
        } else {
            return node; // Node found
        }
    }

    // Delete a node by its value
    delete(value) {
        this.root = this.deleteNode(this.root, value);
        this.size--;
    }

    // Helper function to delete a node
    deleteNode(node, value) {
        if (node === null) {
            return null;
        }
        if (value < node.value) {
            node.left = this.deleteNode(node.left, value);
        } else if (value > node.value) {
            node.right = this.deleteNode(node.right, value);
        } else {
            // Node found
            if (node.left === null) {
                return node.right;
            } else if (node.right === null) {
                return node.left;
            }
            node.value = this.minNode(node.right).value; // Replace with the smallest value in the right subtree
            node.right = this.deleteNode(node.right, node.value);
        }
        return node;
    }

    // Helper function to find the minimum node
    minNode(node) {
        while (node && node.left !== null) {
            node = node.left;
        }
        return node;
    }

    // In-order traversal (left, root, right)
    inOrder() {
        this.inOrderTraverseNode(this.root);
    }

    // Helper function for in-order traversal
    inOrderTraverseNode(node) {
        if (node !== null) {
            this.inOrderTraverseNode(node.left);
            console.log(node.value);
            this.inOrderTraverseNode(node.right);
        }
    }

    // Get the size of the BST
    size() {
        return this.size;
    }
}
```

---

## Example Usage  

```javascript
// Initialize the binary search tree
const bst = new BinarySearchTree();

// Insert values into the BST
bst.insert(10);
bst.insert(20);
bst.insert(5);
bst.insert(15);

// Search for a value in the BST
console.log(bst.search(10)); // Output: Node with value 10
console.log(bst.search(25)); // Output: null

// In-order traversal (prints values in ascending order)
bst.inOrder(); // Output: 5, 10, 15, 20

// Delete a value from the BST
bst.delete(10);
bst.inOrder(); // Output: 5, 15, 20

// Get the size of the BST
console.log(bst.size()); // Output: 3
```

---

## Real-World Applications  
1. **Database Indexing**: Used to quickly locate records in a database.  
2. **Search Engines**: For storing and retrieving web pages or documents based on keywords.  
3. **Autocomplete**: Used in search suggestions and word prediction.  
4. **Priority Queues**: For managing tasks based on priority.  

---

## TikTok Tutorial 🎥  
Want to see a quick tutorial on how to build this? Check out this TikTok video:  
[]()  

---

## How to Run the Code  
1. Clone the repository:  
   ```bash
   git clone https://github.com/your-username/binary-search-tree.git
   cd binary-search-tree
   ```
2. Open the file `binary-search-tree.js` in your favorite code editor.  
3. Run the file using Node.js:  
   ```bash
   node binary-search-tree.js
   ```

---

## Contributing  
Contributions are welcome! If you have suggestions or want to add new features, feel free to create a pull request.  

---

## License  
This project is licensed under the MIT License.  

---

## Connect with Me:
- [LinkedIn - Vitalii Semianchuk](https://www.linkedin.com/in/vitalii-semianchuk-9812a786/)
- [Telegram - @jsmentorfree](https://t.me/jsmentorfree) - We do a lot of free teaching on this channel! Join us to learn and grow in web development.
- [Tiktok - @jsmentoring](https://www.tiktok.com/@jsmentoring) Everyday new videos
- [Youtube - @jsmentor-uk](https://www.youtube.com/@jsmentor-uk) Mentor live streams
- [Dev.to - fix2015](https://dev.to/fix2015) Javascript featured, live, experience but about Binary Search Tree
