**Question**

Huffman coding assigns variable length codewords to fixed length input characters based on their frequencies. More frequent characters are assigned shorter codewords and less frequent characters are assigned longer codewords. A Huffman tree is made for the input string and characters are decoded based on their position in the tree. We add a '0' to the codeword when we move left in the binary tree and a '1' when we move right in the binary tree. We assign codes to the leaf nodes which represent the input characters.

Input characters are only present on the leaves. Internal nodes have a character value of ϕ. Codewords:

A - 1
B - 00
C - 01

No codeword appears as a prefix of any other codeword. Huffman encoding is a prefix free encoding technique.

Encoded String "1001011" represents the string "ABACA"

You have to decode an encoded string using the Huffman tree.

You are given a pointer to the root of the Huffman tree and a binary coded string. You need to print the actual string.

**Input Format**

You are given a function:

```cpp
void decode_huff(node * root, string s) {

}
```

`Note:` Internal nodes have data='\0' (ϕ).

**Output Format**

Output the decoded string on a single line.

**Answer**

```cpp
void decode_huff(node * root, string s) {
    node* current = root;
    for (char c : s) {
        if (c == '0') {
            current = current->left;
        } else {
            current = current->right;
        }

        if (current->left == nullptr && current->right == nullptr) {
            cout << current->data;
            current = root;
        }
    }
}
```
