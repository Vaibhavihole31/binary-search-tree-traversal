
**Pre-order Traversal:**

In pre-order traversal, we also follow a specific order to visit the nodes of a binary tree. Here, we start by visiting the current node first, then the left subtree, and finally the right subtree. Imagine you are exploring a tree starting from the root node and moving towards the lower levels. For each node, you first visit the current node, then visit all the nodes in its left subtree, and lastly visit all the nodes in its right subtree. In simple terms, you visit the current node first, then the left side, and finally the right side.

```
        4
       / \
      2   6
     / \ / \
    1  3 5  7

```

**Pre-order traversal: 4, 2, 1, 3, 6, 5, 7**

Let's go through each traversal to see how the nodes are visited:

* Start from the root node (4).
* Visit the root node 4.
* Visit node 2.
* Visit node 1.
* Visit node 3.
* Visit node 6.
* Visit node 5.
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

void preOrderTraversal(Node *root)
{
    if(root == NULL)
    {
        return;
    }
    
    cout<<root->data<<", ";
    preOrderTraversal(root->left);
    preOrderTraversal(root->right);
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

    preOrderTraversal(root);

    return 0;
}
```

**Output :**

4, 2, 1, 3, 6, 5, 7, 

We define a class called `Node` to represent nodes in a binary tree. Each node contains an integer value (`data`) and two pointers (`left` and `right`) to its left and right child nodes, respectively.

Within the `Node` class, there is a constructor that initializes the `data` value and sets both the `left` and `right` pointers to `NULL`.

Next, we define a function named `preOrderTraversal` that performs an in-order traversal of a binary tree. It takes a pointer to the `root` node as a parameter.

In the `preOrderTraversal` function, we check if the `root` node is `NULL`. If it is, we simply return and exit the function.

If the `root` node is not `NULL`, we first print the `data` value of the `root` node, then recursively call `preOrderTraversal` on the left child of the `root` node, and finally recursively call `preOrderTraversal` on the right child of the `root` node. This follows the in-order traversal order (left subtree, current node, right subtree).

In the `main` function, we create the binary tree by instantiating `Node` objects and connecting them using the `left` and `right` pointers.

We create the `root` node with a value of 4 and then create the other nodes with their respective values.

We establish the relationships between the nodes by assigning the appropriate nodes to the `left` and `right` pointers of their parent nodes.

Finally, we call the `preOrderTraversal` function, passing the `root` node as an argument, to perform an in-order traversal of the binary tree. The `preOrderTraversal` function will print the node values in ascending order.

The program ends by returning 0, indicating successful execution.

