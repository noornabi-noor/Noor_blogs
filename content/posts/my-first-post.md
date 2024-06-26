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