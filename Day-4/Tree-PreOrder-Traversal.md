**Question**

Complete the `preOrder` function, which takes a pointer to the root of a binary tree as its parameter. The function should print the values in the tree's preorder traversal as a single line of space-separated values.

**Input Format**

The `preOrder` function is called with the root node of a binary tree.

**Constraints**

1 <= Number of nodes in the tree <= 500

**Output Format**

Print the preorder traversal of the tree as a single line of space-separated values.

**Answer**

```cpp
void preOrder(Node *root) {
    if (root == NULL) {
        return;
    }

    cout << root->data << " ";

    preOrder(root->left);
    preOrder(root->right);
}
```
