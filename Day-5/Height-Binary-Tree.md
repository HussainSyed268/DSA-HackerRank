**Question**

The height of a binary tree is defined as the number of edges between the tree's root and its furthest leaf.

Function Description

Complete the `getHeight` (or `height`) function in the editor. It must return the height of a binary tree as an integer.

`getHeight` (or `height`) has the following parameter:

- `root`: a reference to the root of a binary tree.

Note: The height of a binary tree with a single node is taken as zero.

**Answer**

```cpp
int height(Node* root) {
    if (root == nullptr) {
        return -1;
    } else {
        int leftHeight = height(root->left);
        int rightHeight = height(root->right);
        return 1 + max(leftHeight, rightHeight);
    }
}

```
