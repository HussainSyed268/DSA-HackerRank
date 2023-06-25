**Question**

In this problem, we need to reverse a doubly linked list. Given a doubly linked list, write a function to reverse the list and return the head node of the reversed list.

**Input Format**

The input consists of the following:

- The number of elements in the linked list.
- The elements of the linked list.

**Output Format**

Return the head of the reversed doubly linked list.

**Example**

Input:

5 // Number of elements of the linked list
1
2
3
4
5

Output:

5
4
3
2
1

**Answer**

```cpp
DoublyLinkedListNode* reverse(DoublyLinkedListNode* llist) {
    vector <DoublyLinkedListNode*> objs;

    while (llist != NULL) {
        objs.push_back(llist);
        llist = llist->next;
    }

    for (int i = objs.size() - 1; i >= 0; i--) {
        objs[i]->next = NULL;
        if (i != 0) {
            objs[i]->prev = NULL;
            objs[i]->next = objs[i - 1];
            objs[i - 1]->prev = objs[i];
        }
    }

    return objs[objs.size() - 1];
}
```
