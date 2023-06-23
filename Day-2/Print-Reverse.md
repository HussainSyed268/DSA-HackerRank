## Question

Given a pointer to the head of a singly-linked list, print each data value from the reversed list. If the given list is empty, do not print anything.

**Example**

`head*` refers to the linked list with data values `1 -> 2 -> 3 -> NULL`

Print the following:

3
2
1

**Function Description**

Complete the `reversePrint` function.

`reversePrint` has the following parameters:

- `SinglyLinkedListNode* head`: a reference to the head of the list

**Prints**

The data values of each node in the reversed list.

**Input Format**

The first line of input contains `t`, the number of test cases.

The input of each test case is as follows:

- The first line contains an integer `n`, the number of elements in the list.
- Each of the next `n` lines contains a data element for a list node.

**Constraints**

- 1 <= n <= 1000
- 1 <= list[i] <= 1000, where `list[i]` is the ith element in the list.

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

void print_singly_linked_list(SinglyLinkedListNode* node, string sep) {
    while (node) {
        cout << node->data;

        node = node->next;

        if (node) {
            cout << sep;
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

/*
 * Complete the 'reversePrint' function below.
 *
 * The function accepts INTEGER_SINGLY_LINKED_LIST llist as parameter.
 */

/*
 * For your reference:
 *
 * SinglyLinkedListNode {
 *     int data;
 *     SinglyLinkedListNode* next;
 * };
 *
 */

void reversePrint(SinglyLinkedListNode* llist) {
    vector<int> vec1;
    vector<int>::iterator p;
    while (llist!=NULL){
        vec1.push_back(llist->data);
        llist = llist->next;
    }
    reverse(vec1.begin(), vec1.end());

    for (p = vec1.begin(); p < vec1.end(); p++) {
        cout << *p << endl;
    }

}

int main()
{
    int tests;
    cin >> tests;
    cin.ignore(numeric_limits<streamsize>::max(), '\n');

    for (int tests_itr = 0; tests_itr < tests; tests_itr++) {
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

        reversePrint(llist->head);
    }

    return 0;
}
```
