# LeetCode Daily Solutions

Welcome to my **LeetCode Daily Solutions** repository! 🚀  
I solve coding problems daily from LeetCode and share my solutions here. Each solution includes well-documented comments to help others understand the approach, logic, and implementation.

---

## Problem: 88. Merge Sorted Array

### Description

You are given two integer arrays `nums1` and `nums2`, sorted in non-decreasing order, and two integers `m` and `n`, representing the number of elements in `nums1` and `nums2` respectively.

The task is to merge `nums1` and `nums2` into a single array sorted in non-decreasing order. The result should be stored inside `nums1`. To accommodate this, `nums1` has a length of `m + n`, where the first `m` elements denote the elements that should be merged, and the last `n` elements are set to `0`.

---

### Examples

#### Example 1:
**Input:**  
`nums1 = [1,2,3,0,0,0]`, `m = 3`, `nums2 = [2,5,6]`, `n = 3`  
**Output:**  
`[1,2,2,3,5,6]`  
**Explanation:**  
The arrays we are merging are `[1,2,3]` and `[2,5,6]`.  
The result is `[1,2,2,3,5,6]`.

#### Example 2:
**Input:**  
`nums1 = [1]`, `m = 1`, `nums2 = []`, `n = 0`  
**Output:**  
`[1]`  

#### Example 3:
**Input:**  
`nums1 = [0]`, `m = 0`, `nums2 = [1]`, `n = 1`  
**Output:**  
`[1]`  

---

### Solution

Here's the solution for the problem in C++:

```cpp
#include <vector>
using namespace std;

class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        // Initialize two pointers for nums1 and nums2
        int l = 0; // Pointer for nums1
        int r = 0; // Pointer for nums2

        // Temporary vector to store the merged elements
        vector<int> temp;

        // Compare elements from nums1 and nums2 and merge them
        while (l < m && r < n) {
            if (nums1[l] <= nums2[r]) {
                temp.push_back(nums1[l]); // Add nums1 element to temp
                l++;
            } else {
                temp.push_back(nums2[r]); // Add nums2 element to temp
                r++;
            }
        }

        // Add remaining elements from nums1 (if any)
        while (l < m) {
            temp.push_back(nums1[l]);
            l++;
        }

        // Add remaining elements from nums2 (if any)
        while (r < n) {
            temp.push_back(nums2[r]);
            r++;
        }

        // Copy the merged elements back to nums1
        for (int i = 0; i < m + n; i++) {
            nums1[i] = temp[i];
        }
    }
};
