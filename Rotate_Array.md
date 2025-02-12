

---

# Rotate Array Problem

## Problem Overview
Given an array `arr[]`, rotate the array to the left (counter-clockwise direction) by `d` steps, where `d` is a positive integer. Perform the rotation **in-place** without using extra space.

## Problem Link
[Rotate Array by N Elements](https://www.geeksforgeeks.org/problems/rotate-array-by-n-elements-1587115621/1)

## Approach

### Modulo Operation
If `d > n` (the length of the array), we first take `d % n` to avoid unnecessary full rotations.

### Reverse Algorithm
The main idea behind solving this problem efficiently is using the **reverse algorithm**, which works as follows:

1. Reverse the first `d` elements of the array.
2. Reverse the remaining `n - d` elements of the array.
3. Reverse the entire array to get the desired rotation.

### Time Complexity
- **Time Complexity**: O(n) where `n` is the size of the array, because we perform three reversals, each taking O(n) time.

### Space Complexity
- **Space Complexity**: O(1) since we are rotating the array in-place without using any extra space.

---

## Code Implementation

### Java Code

```java
// Driver Code Starts
import java.io.*;
import java.util.*;

class GFG {
    public static void main(String args[]) throws IOException {
        BufferedReader in = new BufferedReader(new InputStreamReader(System.in));
        PrintWriter out = new PrintWriter(System.out);

        int t = Integer.parseInt(in.readLine().trim());
        while (t-- > 0) {
            String line = in.readLine();
            String[] tokens = line.split(" ");
            ArrayList<Integer> array = new ArrayList<>();

            // Parse the tokens into integers and add to the array
            for (String token : tokens) {
                array.add(Integer.parseInt(token));
            }

            int d = Integer.parseInt(in.readLine().trim()); // rotation count (key)
            int n = array.size();
            int[] arr = new int[n];
            for (int i = 0; i < n; i++) arr[i] = array.get(i);

            new Solution().rotateArr(arr, d); // rotating the array
            StringBuilder sb = new StringBuilder();

            // printing the elements of the array
            for (int value : arr) sb.append(value).append(" ");
            out.println(sb.toString().trim());

            out.println("~");
        }
        out.flush();
        out.close();
    }
}

// User function Template for Java

class Solution {
    // Function to rotate an array by d elements in counter-clockwise direction.
    static void rotateArr(int arr[], int d) {
        int n = arr.length;
        d = d % n; // Handle cases where d > n

        // Step 1: Reverse first d elements
        reverse(arr, 0, d - 1);
        
        // Step 2: Reverse remaining elements
        reverse(arr, d, n - 1);
        
        // Step 3: Reverse entire array
        reverse(arr, 0, n - 1);
    }

    private static void reverse(int[] arr, int start, int end) {
        while (start < end) {
            int temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;
            start++;
            end--;
        }
    }
}
```

---

## Test Cases

### Example 1
**Input:**
```
arr[] = [1, 2, 3, 4, 5], d = 2
```

**Output:**
```
[3, 4, 5, 1, 2]
```
**Explanation**: After rotating the array by 2 elements, it becomes `[3, 4, 5, 1, 2]`.

---

### Example 2
**Input:**
```
arr[] = [2, 4, 6, 8, 10, 12, 14, 16, 18, 20], d = 3
```

**Output:**
```
[8, 10, 12, 14, 16, 18, 20, 2, 4, 6]
```
**Explanation**: After rotating the array by 3 elements, it becomes `[8, 10, 12, 14, 16, 18, 20, 2, 4, 6]`.

---

### Example 3
**Input:**
```
arr[] = [7, 3, 9, 1], d = 9
```

**Output:**
```
[3, 9, 1, 7]
```
**Explanation**: After rotating the array 9 times, it becomes `[3, 9, 1, 7]`.

---

## Constraints
- `1 <= arr.size(), d <= 10^5`
- `0 <= arr[i] <= 10^5`

---

## Key Points
- This approach uses **constant space** and handles large arrays effectively within **O(n)** time.
- The **reverse technique** ensures that rotations are done efficiently, avoiding extra space for another array or list.
- Feel free to use this approach to rotate arrays efficiently in your future problems! 🚀

--- 

