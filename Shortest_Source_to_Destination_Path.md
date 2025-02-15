## Shortest Source to Destination Path

### **Problem Statement**

Given a **2D binary matrix** `A` of dimensions `N x M`, find the **minimum number of steps** required to reach from **(0,0) to (X, Y).**

### **Constraints:**
- You can **only move** left, right, up, and down.
- You can **only move through cells** that contain `1`.
- If the cell **(0,0) contains `0`**, return `-1`.

### **Example**

#### **Input:**
```plaintext
N = 3, M = 4
A = [[1,0,0,0],
     [1,1,0,1],
     [0,1,1,1]]
X = 2, Y = 3
```
#### **Output:**
```plaintext
5
```
#### **Explanation:**
The shortest path is: 
```
(0,0) -> (1,0) -> (1,1) -> (2,1) -> (2,2) -> (2,3)
```

---

### **Approach**
The problem is solved using **Breadth-First Search (BFS)** because BFS is optimal for finding the shortest path in an **unweighted grid**.

#### **Steps:**
1. **Check Base Case:** If the start `(0,0)` or destination `(X,Y)` is blocked, return `-1`.
2. **BFS Traversal:**
   - Use a **queue** to store `{row, col, distance}`.
   - Start from `(0,0)` and mark it as **visited**.
   - Explore four possible directions (**up, down, left, right**).
   - If a **valid unvisited** path exists, push it into the queue with an incremented distance.
3. **Return Distance:**
   - If we reach `(X, Y)`, return the **distance**.
   - If BFS completes **without finding** `(X, Y)`, return `-1`.

---

### **Complexity Analysis**
- **Time Complexity:** `O(N * M)` (Each cell is visited at most once)
- **Space Complexity:** `O(N * M)` (Queue and visited array)

---

### **Code Implementation (Java)**

```java
import java.util.*;

class Solution {
    static class Cell {
        int x, y, dist;
        Cell(int x, int y, int dist) {
            this.x = x;
            this.y = y;
            this.dist = dist;
        }
    }
    
    public int shortestDistance(int N, int M, int[][] A, int X, int Y) {
        if (A[0][0] == 0 || A[X][Y] == 0) return -1;
        
        int[] dRow = {-1, 1, 0, 0};
        int[] dCol = {0, 0, -1, 1};
        boolean[][] visited = new boolean[N][M];
        Queue<Cell> queue = new LinkedList<>();
        
        queue.add(new Cell(0, 0, 0));
        visited[0][0] = true;
        
        while (!queue.isEmpty()) {
            Cell current = queue.poll();
            int row = current.x, col = current.y, dist = current.dist;
            
            if (row == X && col == Y) return dist;
            
            for (int i = 0; i < 4; i++) {
                int newRow = row + dRow[i];
                int newCol = col + dCol[i];
                
                if (newRow >= 0 && newRow < N && newCol >= 0 && newCol < M && A[newRow][newCol] == 1 && !visited[newRow][newCol]) {
                    queue.add(new Cell(newRow, newCol, dist + 1));
                    visited[newRow][newCol] = true;
                }
            }
        }
        
        return -1;
    }
}
```

---

### **Related Links**
- [Problem Link](https://www.geeksforgeeks.org/problems/shortest-source-to-destination-path3544/1)
- [Breadth-First Search (BFS) Explanation](https://www.geeksforgeeks.org/breadth-first-search-or-bfs-for-a-graph/)
