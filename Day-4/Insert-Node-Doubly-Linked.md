**Question**

We have to insert a node into a sorted doubly linked list. Given a sorted doubly linked list and a node to be inserted, write a function to insert the node into the correct position in the list while maintaining the sorted order.

**Input Format**

The input consists of the following:

- The number of elements in the linked list.
- The elements of the linked list.
- The node to be inserted.

**Output Format**

Print the elements of the doubly linked list after inserting the node in sorted order.

**Example**

Input:

5 // Number of elements of the linked list
1
2
5
10
12
4 // Node to be inserted

Output:

1
2
4
5
10
12

**Answer**

```cpp
DoublyLinkedListNode* sortedInsert(DoublyLinkedListNode* llist, int data) {
    DoublyLinkedListNode* ret = llist;
    DoublyLinkedListNode* node1 = new DoublyLinkedListNode(data);

    if (llist == NULL) {
        return node1;
    }

    if (data <= llist->data) {
        node1->next = llist;
        llist->prev = node1;
        return node1;
    }

    while (llist->next != NULL) {
        if (llist->data <= data && llist->next->data > data) {
            node1->prev = llist;
            node1->next = llist->next;
            llist->next->prev = node1;
            llist->next = node1;
            return ret;
        }
        llist = llist->next;
    }

    llist->next = node1;
    node1->prev = llist;
    node1->next = NULL;
    return ret;
}
```
