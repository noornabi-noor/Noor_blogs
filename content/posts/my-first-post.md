+++
title = "What is Binary Search?"
date = 2024-06-26T09:55:22+06:00
draft = false
+++

Binary search is an efficient algorithm for finding an item from a sorted list of items. It works by repeatedly dividing the search interval in half. If the value of the search key is less than the item in the middle of the interval, the algorithm narrows the interval to the lower half. Otherwise, it narrows it to the upper half. This process continues until the value is found or the interval is empty.

## How Binary Search Works
**1. Initial Setup:**
- Assume we have a sorted array 'A' and we want to find the index of a target value 'T'.

**2. Iterative Steps:**
- Set two pointers, 'low' and 'high', to the beginning and end of the array, respectively.
- Compute the middle index 'mid' as (low + high) // 2.
- Compare the middle element A[mid] with the target 'T'.
- If A[mid] == T, return mid (the target is found).
- If A[mid] < T, set low = mid + 1 (discard the left half).
- If A[mid] > T, set high = mid - 1 (discard the right half).
- Repeat the process until low is greater than high.

**Example:**
> Suppose we have a sorted array {1, 3, 5, 7, 9, 11, 13} and we want to find the index of the value 7.

- Start with low = 0 and high = 6.
- Compute mid = (0 + 6) // 2 = 3.
- Compare A[3] (which is 7) with 7.
- Since A[3] == 7, the index 3 is returned.

      
### C++ Implementation

```cpp
#include <iostream>
#include <vector>

using namespace std;

// Binary search function
int binarySearch(vector<int>& arr, int target) {
    int low = 0;
    int high = arr.size() - 1;

    while (low <= high) {
        int mid = low + (high - low) / 2;

        if (arr[mid] == target)
            return mid;
        else if (arr[mid] < target)
            low = mid + 1;
        else
            high = mid - 1;
    }

    return -1; // Target not found
}

// Example usage for 0 base indexing
int main() {
    vector<int> arr = {1, 3, 5, 7, 9, 11, 13};
    int target = 7;
    int index = binarySearch(arr, target);

    if (index != -1)
        cout << "Index of " << target << ": " << index << endl;
    else
        cout << "Target " << target << " not found in the array." << endl;

    return 0;
}

```

**Why Use Binary Search?**
- Efficiency: Binary search has a time complexity of O(logn), which is much faster than linear search's O(n) for large datasets.
- Sorted Data: It requires the dataset to be sorted, which is a common scenario in many applications like database indexing, searching in dictionaries, and more.

### Practice some problem depends on Binary Search
1. [Minimum time to fulfil all orders] (https://www.geeksforgeeks.org/problems/minimum-time-to-fulfil-all-orders/1?page=1category%255B%255D=Binary%2520Search&sortBy=accuracy)

2. [Max min Height] (https://www.geeksforgeeks.org/problems/max-min-height--170647/1)
3. [Aggressive Cows] (https://www.geeksforgeeks.org/problems/aggressive-cows/1?page=1&category%255B%255D=Binary%2520Search&sortBy=accuracy)
4. [Split Array Largest Sum] (https://www.geeksforgeeks.org/problems/split-array-largest-sum--141634/1)
5. [Square root of a number] (https://www.geeksforgeeks.org/problems/square-root/1?page=1&category%255B%255D=Binary%2520Search&sortBy=accuracy)
6. [Farthest number] (https://www.geeksforgeeks.org/problems/farthest-number--170636/1)
7. [Left most and right most index] (https://www.geeksforgeeks.org/problems/find-first-and-last-occurrence-of-x0849/1?page=2&category%255B%255D=Binary%2520Search&sortBy=accuracy)
8. [Counting elements in two arrays] (https://www.geeksforgeeks.org/problems/counting-elements-in-two-arrays/1?page=2&category%255B%255D=Binary%2520Search&sortBy=accuracy)
9. [EKO] (https://www.spoj.com/problems/EKO/)
10. [Max Consecutive Ones III] (https://leetcode.com/problems/max-consecutive-ones-iii/)
11. [Maximize the Confusion of an Exam] (https://leetcode.com/problems/maximize-the-confusion-of-an-exam/)
12. [Capacity To Ship Packages Within D Days] (https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/)
13. [Find the Distance Value Between Two Arrays] (https://leetcode.com/problems/find-the-distance-value-between-two-arrays/description/)
14. [Maximum Tastiness of Candy Basket] (https://leetcode.com/problems/maximum-tastiness-of-candy-basket/description/)
15. [Minimum Limit of Balls in a Bag] (https://leetcode.com/problems/minimum-limit-of-balls-in-a-bag/description/)


# Binary Search in 2D Array

> Binary search is a widely used algorithm due to its efficiency in finding an element in a sorted array. While it's straightforward to implement binary search in a 1D array, it can be extended to a 2D array as well, given the array meets certain conditions. This post will explain how to perform binary search in a 2D array and provide a sample implementation in C++.

### Conditions for Binary Search in a 2D Array
> For binary search to work in a 2D array, the array must be sorted. The common condition is:

- Each row is sorted in ascending order.
- The first integer of each row is greater than the last integer of the previous row.

### Algorithm Explanation
1. Flatten the 2D Array: Treat the 2D array as a 1D array. We can calculate the middle element by considering the entire array as a single sorted list.
2. Calculate Indices: Convert the middle index back to 2D indices to access the element.
3. Compare and Adjust: Compare the target element with the middle element and adjust the search range accordingly.

### Implementation in C++
Here is a C++ implementation of binary search in a 2D array:

```cpp
#include <iostream>
#include <vector>

bool binarySearch2D(const std::vector<std::vector<int>>& matrix, int target) {
    if (matrix.empty() || matrix[0].empty()) {
        return false;
    }
    
    int rows = matrix.size();
    int cols = matrix[0].size();
    int left = 0;
    int right = rows * cols - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        int midElement = matrix[mid / cols][mid % cols];
        
        if (midElement == target) {
            return true;
        } else if (midElement < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return false;
}

int main() {
    std::vector<std::vector<int>> matrix = {
        {1, 3, 5, 7},
        {10, 11, 16, 20},
        {23, 30, 34, 60}
    };
    int target = 3;
    bool result = binarySearch2D(matrix, target);
    std::cout << (result ? "Found" : "Not Found") << std::endl;
    
    return 0;
}
```

### Explanation of the Code
1. Initialization: Pointers left and right are initialized to the start and end of the flattened array, respectively.
2. Mid Calculation: The middle index is calculated and converted to 2D indices to get the middle element.
3. Comparison and Adjustment: The middle element is compared with the target. If it matches, true is returned. If the middle element is less than the target, the left pointer is adjusted. Otherwise, the right pointer is adjusted.
4. Termination: The loop continues until left exceeds right. If the target is not found, false is returned.

 This method ensures an optimal time complexity of O(log(m * n)), where m is the number of rows and n is the number of columns.

 ### Step-by-Step Explanation

1. Initialization:
- rows = 3 (number of rows in the matrix)
- cols = 4 (number of columns in the matrix)
- left = 0 (starting index in the flattened array)
- right = 11 (ending index in the flattened array, calculated as rows * cols - 1)
2. First Iteration:
- Calculate the middle index: mid = (left + right) / 2 = (0 + 11) / 2 = 5
- Convert mid to 2D indices: mid_row = 5 / 4 = 1 and mid_col = 5 % 4 = 1
- Get the middle element: matrix[1][1] = 11
- Compare mid_element with target:
    - 11 (mid_element) is greater than 3 (target), so update right to mid - 1 = 4
3. Second Iteration:
- Calculate the new middle index: mid = (left + right) / 2 = (0 + 4) / 2 = 2
- Convert mid to 2D indices: mid_row = 2 / 4 = 0 and mid_col = 2 % 4 = 2
- Get the middle element: matrix[0][2] = 5
- Compare mid_element with target:
    - 5 (mid_element) is greater than 3 (target), so update right to mid - 1 = 1
4. Third Iteration:
- Calculate the new middle index: mid = (left + right) / 2 = (0 + 1) / 2 = 0
- Convert mid to 2D indices: mid_row = 0 / 4 = 0 and mid_col = 0 % 4 = 0
- Get the middle element: matrix[0][0] = 1
- Compare mid_element with target:
    - 1 (mid_element) is less than 3 (target), so update left to mid + 1 = 1
5. Fourth Iteration:
- Calculate the new middle index: mid = (left + right) / 2 = (1 + 1) / 2 = 1
- Convert mid to 2D indices: mid_row = 1 / 4 = 0 and mid_col = 1 % 4 = 1
- Get the middle element: matrix[0][1] = 3
- Compare mid_element with target:
    - 3 (mid_element) is equal to 3 (target), so return true

The binary search successfully finds the target 3 in the matrix at position (0, 1).

 ### Practice some problem depends on Binary Search of 2D array

 1. [Median in a row-wise sorted Matrix] (https://www.geeksforgeeks.org/problems/median-in-a-row-wise-sorted-matrix1527/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=median-in-a-row-wise-sorted-matrix)
 2. [Find a Peak Element II] (https://leetcode.com/problems/find-a-peak-element-ii/description/)
 3. [Search a 2D Matrix] (https://leetcode.com/problems/search-a-2d-matrix/description/)
 4. [Search a 2D Matrix II] (https://leetcode.com/problems/search-a-2d-matrix-ii/description/)
 5. [Row with max 1s] (https://www.geeksforgeeks.org/problems/row-with-max-1s0023/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=row-with-max-1s)