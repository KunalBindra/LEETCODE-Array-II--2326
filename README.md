# LEETCODE-Array-II-2326
Let's walk through a dry run of your `spiralMatrix` function step-by-step with some example inputs. Here's how it works:

## Inputs:
- `m = 3` (number of rows)
- `n = 4` (number of columns)
- `head = 1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8 -> 9 -> null` (a linked list with 9 elements)

## Initial Setup:
- We create a 2D array `dp` of size `m x n` initialized to `-1`:
  ```java
  dp = [
         [-1, -1, -1, -1],
         [-1, -1, -1, -1],
         [-1, -1, -1, -1]
       ]
  ```
- Define the boundaries: `top = 0`, `down = m - 1 = 2`, `left = 0`, `right = n - 1 = 3`
- Initialize `id = 0` (to keep track of which direction we are filling)

---

### **First iteration (id = 0):**
- Moving left to right (row `top = 0`):
  - Fill row `0` from `left = 0` to `right = 3` with values from the linked list:
    - `dp[0][0] = 1`, `dp[0][1] = 2`, `dp[0][2] = 3`, `dp[0][3] = 4`
  - Move `top++` (now `top = 1`), adjust the boundary.
- Updated `dp`:
  ```java
  dp = [
         [1, 2, 3, 4],
         [-1, -1, -1, -1],
         [-1, -1, -1, -1]
       ]
  ```

### **Second iteration (id = 1):**
- Moving top to bottom (column `right = 3`):
  - Fill column `3` from `top = 1` to `down = 2`:
    - `dp[1][3] = 5`, `dp[2][3] = 6`
  - Move `right--` (now `right = 2`), adjust the boundary.
- Updated `dp`:
  ```java
  dp = [
         [1, 2, 3, 4],
         [-1, -1, -1, 5],
         [-1, -1, -1, 6]
       ]
  ```

### **Third iteration (id = 2):**
- Moving right to left (row `down = 2`):
  - Fill row `2` from `right = 2` to `left = 0`:
    - `dp[2][2] = 7`, `dp[2][1] = 8`, `dp[2][0] = 9`
  - Move `down--` (now `down = 1`), adjust the boundary.
- Updated `dp`:
  ```java
  dp = [
         [1, 2, 3, 4],
         [-1, -1, -1, 5],
         [9, 8, 7, 6]
       ]
  ```

### **Fourth iteration (id = 3):**
- Moving bottom to top (column `left = 0`):
  - Now `dp[1][0] = -1`, but `head` is `null`, so the while loop exits.

### Final `dp`:
```java
dp = [
       [1, 2, 3, 4],
       [-1, -1, -1, 5],
       [9, 8, 7, 6]
     ]
```

### Summary:
- The spiral order filling of the linked list into the 2D matrix completed successfully.
- The remaining elements in the matrix are left as `-1` since the list ended.
