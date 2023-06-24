**Question**

Given a pointer to the head of a linked list and a specific position, determine the data value at that position. Count backwards from the tail node. The tail is at position 0, its parent is at 1, and so on.

Example:

head refers to 3 -> 2 -> 1 -> 0 -> NULL
positionFromTail = 2

Each of the data values matches its distance from the tail. The value 2 is at the desired position.

Complete the `getNode` function in the editor below.

`getNode` has the following parameters:

- `SinglyLinkedListNode* head`: Refers to the head of the list.
- `int positionFromTail`: The position from the tail to retrieve the value of.

**Returns**

- `int`: The value at the desired position.

**Input Format**

The first line contains an integer `t`, the number of test cases.

Each test case has the following format:

- The first line contains an integer `n`, the number of elements in the linked list.
- The next `n` lines contain an integer, the data value for an element of the linked list.
- The last line contains an integer `positionFromTail`, the position from the tail to retrieve the value of.

**Answer**

```cpp
SinglyLinkedListNode* reverse(SinglyLinkedListNode* llist) {
    if (llist == NULL || llist->next == NULL) {
        return llist;
    }

    SinglyLinkedListNode* prev = NULL;
    SinglyLinkedListNode* current = llist;
    SinglyLinkedListNode* next = NULL;

    while (current != NULL) {
        next = current->next;
        current->next = prev;
        prev = current;
        current = next;
    }

    return prev;
}

int getNode(SinglyLinkedListNode* llist, int positionFromTail) {
    SinglyLinkedListNode* test = reverse(llist);

    for(int i = 0; i < positionFromTail; i++) {
        test = test->next;
    }

    return test->data;
}
```
