## Reverse an Array of Integers

An array is a type of data structure that stores elements of the same type in a contiguous block of memory. In an array A, of size N, each memory location has some unique index i (where 0 <= i < N) that can be referenced as A[i].

### Problem

Reverse an array of integers.

### Example

Given the array A = [1, 2, 3], the reversed array would be [3, 2, 1].

### Function Description

Complete the function `reverseArray` in the editor below.

`reverseArray` has the following parameter:

- `vector<int> a`: the array to reverse

It is expected to return an `vector<int>`, the reversed array.

### Input Format

The first line contains an integer N, the number of integers in array A.
The second line contains N space-separated integers that make up array A.

### Solution

Here's the C++ code that solves the problem:

```cpp
#include <bits/stdc++.h>

using namespace std;

vector<int> reverseArray(vector<int> a) {
    vector<int> vec1;
    for (int i = a.size() - 1; i >= 0; i--) {
        vec1.push_back(a[i]);
    }
    return vec1;
}

int main() {
    // Read input
    int arr_count;
    cin >> arr_count;
    vector<int> arr(arr_count);
    for (int i = 0; i < arr_count; i++) {
        cin >> arr[i];
    }

    // Reverse the array
    vector<int> res = reverseArray(arr);

    // Print the reversed array
    for (size_t i = 0; i < res.size(); i++) {
        cout << res[i];
        if (i != res.size() - 1) {
            cout << " ";
        }
    }
    cout << endl;

    return 0;
}
```
