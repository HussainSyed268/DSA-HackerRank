## Question

You’re given the pointer to the head node of a linked list and the position of a node to delete. Delete the node at the given position and return the head node. A position of 0 indicates the head, a position of 1 indicates one node away from the head, and so on. The list may become empty after you delete the node.

**Input Format**

You have to complete the `Node* Delete(Node* head, int position)` method which takes two arguments - the head of the linked list and the position of the node to delete. You should NOT read any input from stdin/console. The position will always be at least 0 and less than the number of elements in the list.

**Output Format**

Delete the node at the given position and return the head of the updated linked list. Do NOT print anything to stdout/console.

**Sample Input**

1 --> 2 --> 3 --> NULL, position = 0
1 --> NULL, position = 0

**Sample Output**

2 --> 3 --> NULL

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

        void insert_node(int node_data) {
            SinglyLinkedListNode* node = new SinglyLinkedListNode(node_data);

            if (!this->head) {
                this->head = node;
            } else {
                this->tail->next = node;
            }

            this->tail = node;
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

SinglyLinkedListNode* deleteNode(SinglyLinkedListNode* llist, int position) {
    SinglyLinkedListNode* temp = llist;
    if (position == 0) {
        SinglyLinkedListNode* temp3 = temp->next;
        delete temp;
        return temp3;
    } else {
        for (int i = 0; i < position - 1; i++) {
            temp = temp->next;
        }
        SinglyLinkedListNode* temp2 = temp->next->next;
        delete temp->next;
        temp->next = temp2;
    }

    return llist;
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

        llist->insert_node(llist_item);
    }

    int position;
    cin >> position;
    cin.ignore(numeric_limits<streamsize>::max(), '\n');

    SinglyLinkedListNode* llist1 = deleteNode(llist->head, position);

    print_singly_linked_list(llist1, " ", fout);
    fout << "\n";

    free_singly_linked_list(llist1);

    fout.close();

    return 0;
}
```
