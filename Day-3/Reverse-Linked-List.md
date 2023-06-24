**Question**

Given the pointer to the head node of a linked list, change the next pointers of the nodes so that their order is reversed. The head pointer given may be null, meaning that the initial list is empty. Manipulate the pointers of each node in place and return the head, now referencing the head of the reversed list.

**Example**

Input:

1 -> 2 -> 3 -> NULL

Output:

3 -> 2 -> 1 -> NULL

**Function Signature**

````cpp
SinglyLinkedListNode* reverse(SinglyLinkedListNode* llist)


**Answer**

```cpp
#include <bits/stdc++.h>

using namespace std;

class SinglyLinkedListNode {
    public:
        int data;
        SinglyLinkedListNode *next;

        SinglyLinkedListNode(int node_data) {
            this->data = node_data;
            this->next = nullptr;
        }
};

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
````
