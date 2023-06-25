**Question**

In this challenge, you are required to implement the inorder traversal of a tree. Complete the `inOrder` function, which takes a pointer to the root of a binary tree as its parameter. The function should print the values in the tree's inorder traversal as a single line of space-separated values.

**Input Format**

The `inOrder` function is called with the root node of a binary tree.

**Constraints**

1 <= Number of nodes in the tree <= 500

**Output Format**

Print the inorder traversal of the tree as a single line of space-separated values.

**Answer**

```cpp
void inOrder(Node *root) {
    if (root == NULL) {
        return;
    }

    inOrder(root->left);
    cout << root->data << " ";
    inOrder(root->right);
}
```
