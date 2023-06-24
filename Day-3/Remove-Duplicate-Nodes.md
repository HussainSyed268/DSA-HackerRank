**Question**

You're given the pointer to the head node of a sorted linked list, where the data in the nodes is in ascending order. Delete as few nodes as possible so that the list does not contain any value more than once. The given head pointer may be null indicating that the list is empty.

**Input Format**

You have to complete the `SinglyLinkedListNode removeDuplicates(SinglyLinkedListNode head)` method which takes one argument – the head of the sorted linked list. You should NOT read any input from stdin/console.

The input is handled by the code in the editor and the format is as follows:

The first line contains an integer `t`, denoting the number of test cases. The format for each test case is as follows:

- The first line contains an integer `n`, denoting the number of elements in the linked list.
- The next `n` lines contain an integer each, denoting the elements of the linked list.

**Constraints**

- 1 <= t <= 10
- 1 <= n <= 1000
- 1 <= list'i <= 1000

**Output Format**

Delete as few nodes as possible to ensure that no two nodes have the same data. Adjust the next pointers to ensure that the remaining nodes form a single sorted linked list. Then return the head of the sorted updated linked list. Do NOT print anything to stdout/console.

The output is handled by the code in the editor and the format is as follows: For each test case, print in a new line, the data of the linked list after removing the duplicates separated by space.

**Answer**

```cpp
SinglyLinkedListNode* removeDuplicates(SinglyLinkedListNode* llist) {
    SinglyLinkedListNode* head = llist;

    while (head != NULL && head->next != NULL) {
        if (head->next->data == head->data) {
            SinglyLinkedListNode* duplicate = head->next;
            head->next = duplicate->next;
            delete duplicate;
        } else {
            head = head->next;
        }
    }

    return llist;
}
```
