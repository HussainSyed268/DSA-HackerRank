**Question**

A level-order traversal, also known as a breadth-first search, visits each level of a tree's nodes from left to right, top to bottom. You are given a pointer `root` pointing to the root of a binary search tree. Complete the `levelOrder` function provided in your editor so that it prints the level-order traversal of the binary search tree.

**Input Format**

The locked stub code in your editor reads the following inputs and assembles them into a BST:

- The first line contains an integer, T, denoting the number of test cases.
- The T subsequent lines each contain an integer, data, denoting the value of an element that must be added to the BST.

**Output Format**

Print the data value of each node in the tree's level-order traversal as a single line of N space-separated integers.

**Answer**

```cpp
void levelOrder(Node* root) {
    if (root == nullptr)
        return;

    queue<Node*> queue;
    queue.push(root);

    while (!queue.empty()) {
        Node* node = queue.front();
        queue.pop();

        cout << node->data << " ";

        if (node->left != nullptr)
            queue.push(node->left);

        if (node->right != nullptr)
            queue.push(node->right);
    }
}
```
