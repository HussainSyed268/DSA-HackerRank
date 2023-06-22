# Hourglass Sum

## Question

Given a 6x6 2D Array `arr`:

1 1 1 0 0 0
0 1 0 0 0 0
1 1 1 0 0 0
0 0 0 0 0 0
0 0 0 0 0 0
0 0 0 0 0 0

We define an hourglass to be a subset of values with indices falling in this pattern in `arr`'s graphical representation:

a b c
d
e f g

There are 16 hourglasses in `arr`, and an hourglass sum is the sum of an hourglass' values. Calculate the hourglass sum for every hourglass in `arr`, then print the maximum hourglass sum.

For example, given the 2D array:

-63, -34, -9, 12,
-10, 0, 28, 23,
-27, -11, -2, 10,
9, 17, 25, 18

Our highest hourglass value is 28 from the hourglass:

0 4 3
1
8 6 6

## Answer

```cpp
#include <bits/stdc++.h>

using namespace std;

int hourglassSum(vector<vector<int>> arr) {
    int sum = INT_MIN;  // Initialize sum to the smallest possible integer

    // Get the dimensions of the matrix
    int rows = arr.size();
    int cols = arr[0].size();

    for (int i = 0; i <= rows - 3; i++) {
        for (int j = 0; j <= cols - 3; j++) {
            int temp = arr[i][j] + arr[i][j + 1] + arr[i][j + 2] +
                       arr[i + 1][j + 1] +
                       arr[i + 2][j] + arr[i + 2][j + 1] + arr[i + 2][j + 2];
            if (temp > sum) {
                sum = temp;
            }
        }
    }

    return sum;
}

int main() {
    vector<vector<int>> arr(6);

    for (int i = 0; i < 6; i++) {
        arr[i].resize(6);

        string arr_row_temp_temp;
        getline(cin, arr_row_temp_temp);

        vector<string> arr_row_temp = split(rtrim(arr_row_temp_temp));

        for (int j = 0; j < 6; j++) {
            int arr_row_item = stoi(arr_row_temp[j]);

            arr[i][j] = arr_row_item;
        }
    }

    int result = hourglassSum(arr);

    cout << result << "\n";

    return 0;
}
```
