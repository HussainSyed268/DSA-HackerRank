## Question

You’re given the pointer to the head node of a linked list and an integer to add to the list. Create a new node with the given integer, insert this node at the head of the linked list, and return the new head node. The head pointer given may be null, meaning that the initial list is empty.

### Input Format

You have to complete the `SinglyLinkedListNode Insert(SinglyLinkedListNode head, int data)` method, which takes two arguments – the head of the linked list and the integer to insert. You should NOT read any input from stdin/console.

The input is handled by the code in the editor and is as follows:

The first line contains an integer `n`, denoting the number of elements to be inserted at the head of the list.
The next `n` lines contain an integer each, denoting the element to be inserted.

**Constraints**

- 1 <= n <= 1000
- 1 <= list <= 1000

### Output Format

Insert the new node at the head and return the head of the updated linked list. Do NOT print anything to stdout/console.

The output is handled by the code in the editor and it is as follows:

Print the elements of the linked list from head to tail, each on a new line.

## Answer

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

class SinglyLinkedList {
    public:
        SinglyLinkedListNode *head;
        SinglyLinkedListNode *tail;

        SinglyLinkedList() {
            this->head = nullptr;
            this->tail = nullptr;
        }

};

void print_singly_linked_list(SinglyLinkedListNode* node, string sep, ofstream& fout) {
    while (node) {
        fout << node->data;

        node = node->next;

        if (node) {
            fout << sep;
        }
    }
}

void free_singly_linked_list(SinglyLinkedListNode* node) {
    while (node) {
        SinglyLinkedListNode* temp = node;
        node = node->next;

        free(temp);
    }
}

SinglyLinkedListNode* insertNodeAtHead(SinglyLinkedListNode* llist, int data) {
    SinglyLinkedListNode* head = new SinglyLinkedListNode(data);

    if (llist == nullptr) {
        llist = head;
    } else {
        head->next = llist;
    }

    return head;
}

int main() {
    ofstream fout(getenv("OUTPUT_PATH"));

    SinglyLinkedList* llist = new SinglyLinkedList();

    int llist_count;
    cin >> llist_count;
    cin.ignore(numeric_limits<streamsize>::max(), '\n');

    for (int i = 0; i < llist_count; i++) {
        int llist_item;
        cin >> llist_item;
        cin.ignore(numeric_limits<streamsize>::max(), '\n');

        SinglyLinkedListNode* llist_head = insertNodeAtHead(llist->head, llist_item);
        llist->head = llist_head;
    }

    print_singly_linked_list(llist->head, "\n", fout);
    fout << "\n";

    free_singly_linked_list(llist->head);

    fout.close();

    return 0;
}
```
