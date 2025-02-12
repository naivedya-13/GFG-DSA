

---

# Non-Repeating Element

## Problem Overview
Given an array `arr[]` of integers, find the **first non-repeating element** in the array. If no non-repeating element is found, return `0`.

### Note:
- The array consists of **only positive and negative integers** and **not zero**.

## Problem Link
[Non-Repeating Element](https://www.geeksforgeeks.org/find-first-non-repeating-element-in-an-array/)

---

## Approach

### Steps:
1. **Count Element Frequency**: Use a hash map to count the frequency of each element in the array.
2. **Find First Non-Repeating Element**: Traverse the array again and return the first element that appears exactly once (frequency of 1).
3. **Return 0 if Not Found**: If no element with a frequency of 1 is found, return `0`.

### Time Complexity:
- **Time Complexity**: O(n), where `n` is the size of the array. We traverse the array twice: once to count frequencies and once to find the first non-repeating element.
  
### Space Complexity:
- **Space Complexity**: O(n), as we are using a hash map to store the frequency of each element in the array.

---

## Code Implementation

### Java Code

```java
// Initial Template for Java
import java.io.*;
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t =
            Integer.parseInt(scanner.nextLine().trim()); // Read number of test cases

        while (t-- > 0) {
            String line = scanner.nextLine().trim(); // Read the entire line
            String[] numsStr = line.split(" "); // Split the line into string numbers
            int[] nums = new int[numsStr.length];
            for (int i = 0; i < numsStr.length; i++) {
                nums[i] =
                    Integer.parseInt(numsStr[i]); // Convert each string to integer
            }

            int ans = new Solution().firstNonRepeating(
                nums); // Compute the result using the Solution class

            System.out.println(ans); // Print the result
            System.out.println("~");
        }
    }
}

// User function Template for Java

class Solution {
    public int firstNonRepeating(int[] arr) {
        // Step 1: Create a map to store the frequency of elements
        HashMap<Integer, Integer> map = new HashMap<>();

        // Count the frequency of each element
        for (int num : arr) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }

        // Step 2: Find the first element with frequency 1
        for (int num : arr) {
            if (map.get(num) == 1) {
                return num; // Return the first non-repeating element
            }
        }

        // Return 0 if no non-repeating element is found
        return 0;
    }
}
```

---

## Test Cases

### Example 1
**Input:**
```
arr[] = [-1, 2, -1, 3, 2]
```

**Output:**
```
3
```
**Explanation**: 
- `-1` and `2` are repeating.
- `3` is the only number occurring once, so the output is `3`.

---

### Example 2
**Input:**
```
arr[] = [1, 1, 1]
```

**Output:**
```
0
```
**Explanation**: 
- All elements are repeating, so the output is `0`.

---

## Constraints:
- `1 <= arr.size <= 10^6`
- `-10^9 <= arr[i] <= 10^9`
- `arr[i] != 0`

---

## Key Points:
- The use of a **hash map** makes it efficient to find the frequency of elements.
- The problem is solved in **O(n)** time complexity, where `n` is the size of the array.
- The solution uses **O(n)** space complexity due to the hash map storing the element frequencies.

--- 
