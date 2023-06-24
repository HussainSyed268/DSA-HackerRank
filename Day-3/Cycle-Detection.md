**Question**

A linked list is said to contain a cycle if any node is visited more than once while traversing the list. Given a pointer to the head of a linked list, determine if it contains a cycle. If it does, return 1. Otherwise, return 0.

**Example**

head refers to the list of nodes 1 -> 2 -> 3 -> NULL

The numbers shown are the node numbers, not their data values. There is no cycle in this list, so return 0.

head refers to the list of nodes 1 -> 2 -> 3 -> 1 -> NULL

There is a cycle where node 3 points back to node 1, so return 1.

**Function Description**

Complete the `has_cycle` function in the editor below.

It has the following parameter:

- `SinglyLinkedListNode* head`: a reference to the head of the list

**Returns**

- `int`: 1 if there is a cycle or 0 if there is not

**Note**: If the list is empty, head will be null.

**Answer**

```cpp
bool has_cycle(SinglyLinkedListNode* head) {
    vector<SinglyLinkedListNode*> ads;
    while(head != NULL){
        if (find(ads.begin(), ads.end(), head) == ads.end()){
            ads.push_back(head);
            head = head->next;
        }
        else{
            return 1;
        }
    }
    return 0;
}
```
