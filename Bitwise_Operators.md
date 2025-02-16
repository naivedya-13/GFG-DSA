# Bitwise Operators

This repository contains a solution for the [Bitwise Operators](https://www.geeksforgeeks.org/problems/bitwise-operators/0) problem from GeeksforGeeks.

## Problem Statement
Given three positive integers `a`, `b`, and `c`, perform the following bitwise operations:

1. `d = a ^ a` (XOR of a number with itself is `0`)
2. `e = c ^ b` (XOR of `c` and `b`)
3. `f = a & b` (Bitwise AND of `a` and `b`)
4. `g = c | (a ^ a)` (Bitwise OR with `0`, resulting in `c`)
5. `h = ~e` (Bitwise NOT of `e`)

The program prints these five values in order.

## Constraints
- `1 <= A, B, C <= 10^6`

## Implementation
The solution is implemented in Java inside the `Geeks` class.

```java
class Geeks {
    static void bitWiseOperation(int a, int b, int c) {
        int d = a ^ a;
        int e = c ^ b;
        int f = a & b;
        int g = c | (a ^ a);
        int h = ~e;
        
        System.out.println(d);
        System.out.println(e);
        System.out.println(f);
        System.out.println(g);
        System.out.println(h);
    }
}
```

## How to Run
1. Clone the repository.
2. Compile and run the Java file using:
   ```sh
   javac Geeks.java
   java Geeks
   ```

## License
This project is licensed under the MIT License.
