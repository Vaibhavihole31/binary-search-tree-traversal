**In-order Traversal:**

In in-order traversal, we follow a specific order to visit the nodes of a binary tree. We start by visiting the left subtree, then the current node, and finally the right subtree. Imagine you are exploring a tree from the left side, moving towards the right side. For each node, you first visit all the nodes in its left subtree, then visit the current node, and lastly visit all the nodes in its right subtree. In simple terms, you visit the left side first, then the current node, and finally the right side. In a binary search tree, the in-order traversal will give you the nodes in ascending order.

**Example :**

```
        4
       / \
      2   6
     / \ / \
    1  3 5  7

```

**In-order traversal: 1, 2, 3, 4, 5, 6, 7**

Let's go through each traversal to see how the nodes are visited:

* Start from the left subtree of the root (4).
* Visit node 1.
* Visit node 2.
* Visit node 3.
* Visit the root node 4.
* Visit node 5.
* Visit node 6.
* Visit node 7.
* End.

**Code :** 

```cpp
#include<iostream>
#include<stack>

using namespace std;

class Node
{
public:
    int data;
    Node *left;
    Node *right;

    Node(int data)
    {
        this->data = data;
        left = NULL;
        right = NULL;
    }
};

void inOrderTraversal(Node *root)
{
    if(root == NULL)
    {
        return;
    }

    inOrderTraversal(root->left);
    cout<<root->data<<", ";
    inOrderTraversal(root->right);
}

int main()
{
    Node *root = new Node(4);
    Node *a = new Node(1);
    Node *b = new Node(2);
    Node *c = new Node(3);
    Node *d = new Node(5);
    Node *e = new Node(6);
    Node *f = new Node(7);

    root->left = b;
    root->right = e;

    b->left = a;
    b->right = c;

    e->left = d;
    e->right = f;

    inOrderTraversal(root);

    return 0;
}
```

**Output :**

1, 2, 3, 4, 5, 6, 7, 

We define a class called `Node` to represent nodes in a binary tree. Each node contains an integer value (`data`) and two pointers (`left` and `right`) to its left and right child nodes, respectively.

Within the `Node` class, there is a constructor that initializes the `data` value and sets both the `left` and `right` pointers to `NULL`.

Next, we define a function named `inOrderTraversal` that performs an in-order traversal of a binary tree. It takes a pointer to the `root` node as a parameter.

In the `inOrderTraversal` function, we check if the `root` node is `NULL`. If it is, we simply return and exit the function.

If the `root` node is not `NULL`, we recursively call `inOrderTraversal` on the left child of the `root` node, then print the `data` value of the `root` node, and finally recursively call inOrderTraversal on the right child of the root node. This follows the in-order traversal order (left subtree, current node, right subtree).

In the `main` function, we create the binary tree by instantiating `Node` objects and connecting them using the `left` and `right` pointers.

We create the `root` node with a value of 4 and then create the other nodes with their respective values.

We establish the relationships between the nodes by assigning the appropriate nodes to the `left` and `right` pointers of their parent nodes.

Finally, we call the `inOrderTraversal` function, passing the `root` node as an argument, to perform an in-order traversal of the binary tree. The `inOrderTraversal` function will print the node values in ascending order.

The program ends by returning 0, indicating successful execution.