**Question**

In this HackerRank problem, we are given pointers to the heads of two linked lists. We need to compare the data of both linked lists and check if they are equal or not. If all the data are the same, then return `1`; otherwise, return `0`.

**Example**

Input:

LinkedList 1: 1 -> 2 -> 3 -> NULL
LinkedList 2: 1 -> 2 -> 3 -> NULL

Output:

1

**Function Signature**

```cpp
bool compare_lists(SinglyLinkedListNode* head1, SinglyLinkedListNode* head2)

```

**Explanation**

To solve this problem, we can iterate through both linked lists simultaneously and compare the data of each node. If we encounter any mismatch, we return `0` indicating that the lists are not equal. If we reach the end of both lists without any mismatches, we return `1` indicating that the lists are equal.

**Solution**

```cpp
bool compare_lists(SinglyLinkedListNode* head1, SinglyLinkedListNode* head2) {
    while (head1 != NULL && head2 != NULL) {
        if (head1->data != head2->data) {
            return 0;
        }
        head1 = head1->next;
        head2 = head2->next;
    }

    // If either list has remaining nodes, they are not equal
    if (head1 != NULL || head2 != NULL) {
        return 0;
    }

    // Both lists are equal
    return 1;
}
```
