## Post-order Traversal:

In post-order traversal, we once again follow a specific order to visit the nodes of a binary tree. This time, we start by visiting the left subtree, then the right subtree, and finally the current node. Imagine you are exploring a tree from the bottom up. For each node, you first visit all the nodes in its left subtree, then visit all the nodes in its right subtree, and lastly visit the current node. In simple terms, you visit the left side first, then the right side, and finally the current node.

```
        4
       / \
      2   6
     / \ / \
    1  3 5  7

```

**Post-order traversal: 1, 3, 2, 5, 7, 6, 4**

Let's go through each traversal to see how the nodes are visited:

* Start from the left subtree of the root (4).
* Visit node 1.
* Visit node 3.
* Visit node 2.
* Visit node 5.
* Visit node 7.
* Visit node 6.
* Visit the root node 4.
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

void postOrderTraversal(Node *root)
{
    if(root == NULL)
    {
        return;
    }
    
    postOrderTraversal(root->left);
    postOrderTraversal(root->right);
    cout<<root->data<<", ";
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

    postOrderTraversal(root);

    return 0;
}
```

**Output :**

1, 3, 2, 5, 7, 6, 4, 

We define a class called `Node` to represent nodes in a binary tree. Each node contains an integer value (`data`) and two pointers (`left` and `right`) to its left and right child nodes, respectively.

Within the `Node` class, there is a constructor that initializes the `data` value and sets both the `left` and `right` pointers to `NULL`.

Next, we define a function named `postOrderTraversal` that performs a post-order traversal of a binary tree. It takes a pointer to the `root` node as a parameter.

In the `postOrderTraversal` function, we check if the `root` `node` is NULL. If it is, we simply return and exit the function.

If the `root` node is not `NULL`, we first recursively call `postOrderTraversal` on the left child of the `root` node, then recursively call it on the right child of the root node, and finally print the `data` value of the `root` node. This follows the post-order traversal order (left subtree, right subtree, current node).

In the `main` function, we create the binary tree by instantiating `Node` objects and connecting them using the `left` and ri`ght pointers.

We create the `root` node with a value of 4 and then create the other nodes with their respective values.

We establish the relationships between the nodes by assigning the appropriate nodes to the `left` and `right` pointers of their parent nodes.

Finally, we call the `postOrderTraversal` function, passing the `root` node as an argument, to perform a post-order traversal of the binary tree. The `postOrderTraversal` function will print the node values according to the post-order traversal order.

The program ends by returning 0, indicating successful execution.