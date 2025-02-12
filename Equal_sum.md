

---

# Equal Sum

## Problem Overview

Given an array `arr[]`, determine if there exists an element such that the sum of the elements on its left is equal to the sum of the elements on its right. If there are no elements to the left/right, then the sum is considered to be zero.

### Example:

**Input 1:**
```
arr[] = [1, 2, 3, 3]
```
**Output 1:**
```
true
```
**Explanation**: 
- For the element at index `i = 3`, the sum of the elements to the left (`1 + 2 = 3`) is equal to the sum of the elements to the right (`3`), so the output is `true`.

**Input 2:**
```
arr[] = [1, 5]
```
**Output 2:**
```
false
```
**Explanation**: 
- There is no index where the left sum equals the right sum.

---

## Approach

### Steps:
1. **Calculate the total sum** of the array.
2. **Traverse the array** and calculate the sum of elements to the left of each element (`leftSum`).
3. For each element, the sum of the elements to the right (`rightSum`) can be calculated as `totalSum - leftSum - arr[i]`.
4. **Check if the left sum equals the right sum**. If true, return `"true"`.
5. If no such index is found after traversing the entire array, return `"false"`.

### Time Complexity:
- **Time Complexity**: O(n), where `n` is the size of the array. We traverse the array twice: once to calculate the total sum and once to find the equilibrium index.
  
### Space Complexity:
- **Space Complexity**: O(1), as we are only using a few extra variables.

---

## Code Implementation

### Java Code

```java
// Initial Template for Java
import java.io.*;
import java.lang.*;
import java.util.*;

class Solution {
    String equilibrium(int arr[]) {
        // Get array length
        int n = arr.length;
        
        // If array has only one element, return "YES"
        if (n == 1) {
            return "true";
        }
        
        // Calculate total sum
        long totalSum = 0;
        for (int num : arr) {
            totalSum += num;
        }
        
        // Initialize left sum
        long leftSum = 0;
        
        // Iterate through array
        for (int i = 0; i < n; i++) {
            // Right sum would be total sum minus current element
            // and left sum
            long rightSum = totalSum - arr[i] - leftSum;
            
            // If left sum equals right sum, we found our answer
            if (leftSum == rightSum) {
                return "true";
            }
            
            // Add current element to left sum for next iteration
            leftSum += arr[i];
        }
        
        // If we reach here, no such element exists
        return "false";
    }
}

class GFG {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int t = Integer.parseInt(br.readLine());
        while (t-- > 0) {
            String line = br.readLine();
            String[] tokens = line.split(" ");

            // Create an ArrayList to store the integers
            ArrayList<Integer> array = new ArrayList<>();

            // Parse the tokens into integers and add to the array
            for (String token : tokens) {
                array.add(Integer.parseInt(token));
            }

            int[] arr = new int[array.size()];
            int idx = 0;
            for (int i : array) arr[idx++] = i;
            Solution obj = new Solution();
            String res = obj.equilibrium(arr);

            System.out.println(res);
            System.out.println("~");
        }
    }
}
```

---

## Test Cases

### Example 1
**Input:**
```
arr[] = [1, 2, 3, 3]
```

**Output:**
```
true
```
**Explanation**: 
- For the element at index `i = 3`, the sum of the elements to the left (`1 + 2 = 3`) is equal to the sum of the elements to the right (`3`), so the output is `true`.

---

### Example 2
**Input:**
```
arr[] = [1, 5]
```

**Output:**
```
false
```
**Explanation**: 
- No element has the sum of the left and right elements equal, so the output is `false`.

---

## Constraints:
- `1 ≤ arr.size() ≤ 10^5`
- `1 ≤ arr[i] ≤ 10^6`

---

## Key Points:
- The solution efficiently calculates the equilibrium index with **O(n)** time complexity by calculating the sum of the array and then iterating through the array once.
- The algorithm only requires **O(1)** extra space, making it memory efficient.

---
