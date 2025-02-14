# Spirally Traversing a Matrix

## Problem Statement
Given a matrix of size **N x M**, the task is to return a list of integers denoting the spiral traversal of the matrix.

## Examples

### Example 1:
**Input:**
```
N = 3, M = 3
mat[][] = [[1, 2, 3],
           [4, 5, 6],
           [7, 8, 9]]
```
**Output:**
```
[1, 2, 3, 6, 9, 8, 7, 4, 5]
```
**Explanation:**
The spiral order of the given matrix is:
1 → 2 → 3 → 6 → 9 → 8 → 7 → 4 → 5

---

### Example 2:
**Input:**
```
N = 4, M = 4
mat[][] = [[1, 2, 3, 4],
           [5, 6, 7, 8],
           [9, 10, 11, 12],
           [13, 14, 15, 16]]
```
**Output:**
```
[1, 2, 3, 4, 8, 12, 16, 15, 14, 13, 9, 5, 6, 7, 11, 10]
```
**Explanation:**
The spiral order of the given matrix is:
1 → 2 → 3 → 4 → 8 → 12 → 16 → 15 → 14 → 13 → 9 → 5 → 6 → 7 → 11 → 10

---

## Constraints:
- `1 ≤ N, M ≤ 100`
- `0 ≤ mat[i][j] ≤ 100`

## Related Topics:
- Matrix Manipulation
- Simulation

## Problem Link:
[Spirally Traversing a Matrix - GeeksforGeeks](https://www.geeksforgeeks.org/problems/spirally-traversing-a-matrix-1587115621/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=practice_card)

## Solution Code:
```java
import java.util.*;

class Solution {
    public ArrayList<Integer> spirallyTraverse(int mat[][]) {
        ArrayList<Integer> result = new ArrayList<>();
        if (mat == null || mat.length == 0) return result;
        
        int rows = mat.length, cols = mat[0].length;
        int top = 0, bottom = rows - 1, left = 0, right = cols - 1;

        while (top <= bottom && left <= right) {
            // Traverse Left to Right (Top Row)
            for (int i = left; i <= right; i++)
                result.add(mat[top][i]);
            top++; // Move down

            // Traverse Top to Bottom (Right Column)
            for (int i = top; i <= bottom; i++)
                result.add(mat[i][right]);
            right--; // Move left

            // Traverse Right to Left (Bottom Row) if still valid
            if (top <= bottom) {
                for (int i = right; i >= left; i--)
                    result.add(mat[bottom][i]);
                bottom--; // Move up
            }

            // Traverse Bottom to Top (Left Column) if still valid
            if (left <= right) {
                for (int i = bottom; i >= top; i--)
                    result.add(mat[i][left]);
                left++; // Move right
            }
        }

        return result;
    }
}
```

