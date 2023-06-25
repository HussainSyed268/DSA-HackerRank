**Question**

Given pointers to the head nodes of two linked lists that merge together at some point, find the node where the two lists merge. It is guaranteed that the two head nodes will be different, and neither will be NULL. Complete the `int FindMergeNode(Node* headA, Node* headB)` method so that it finds and returns the data value of the node where the two lists merge.

**Input Format**

The `FindMergeNode(Node*, Node*)` method has two parameters, `headA` and `headB`, which are the non-null head nodes of two separate linked lists that are guaranteed to converge. Do not read any input from stdin/console.

**Output Format**

Each node has a data field containing an integer; return the integer data for the node where the two lists converge. Do not write any output to stdout/console.

**Example**

```cpp
int findMergeNode(SinglyLinkedListNode* head1, SinglyLinkedListNode* head2) {
    int count1 = 0;
    int count2 = 0;
    SinglyLinkedListNode* temp1 = head1;
    SinglyLinkedListNode* temp2 = head2;

    while (temp1 != NULL) {
        count1++;
        temp1 = temp1->next;
    }

    while (temp2 != NULL) {
        count2++;
        temp2 = temp2->next;
    }

    temp1 = head1;
    temp2 = head2;

    if (count1 > count2) {
        int diff = count1 - count2;
        for (int i = 0; i < diff; i++) {
            temp1 = temp1->next;
        }
    } else if (count1 < count2) {
        int diff = count2 - count1;
        for (int i = 0; i < diff; i++) {
            temp2 = temp2->next;
        }
    }

    while (temp1 != NULL && temp2 != NULL) {
        if (temp1 == temp2) {
            return temp1->data;
        }
        temp1 = temp1->next;
        temp2 = temp2->next;
    }

    return -1;
}
```
