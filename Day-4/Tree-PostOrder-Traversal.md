**Question**

Complete the `postOrder` function, which takes a pointer to the root of a binary tree as its parameter. The function should print the values in the tree's postorder traversal as a single line of space-separated values.

**Input Format**

The `postOrder` function is called with the root node of a binary tree.

**Constraints**

1 <= Number of nodes in the tree <= 500

**Output Format**

Print the postorder traversal of the tree as a single line of space-separated values.

**Answer**

```cpp
void postOrder(Node *root) {
    if (root == NULL) {
        return;
    }

    postOrder(root->left);
    postOrder(root->right);
    cout << root->data << " ";
}
```
