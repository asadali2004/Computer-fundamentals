# 📦 Arrays in Java — Complete Mastery Guide

> **🎯 Master Linear Data Structures**: From fundamentals to advanced interview prep.

---

## 🔰 Part 1: Array Fundamentals

### 📖 What is an Array?

An **array** is a **container object** that holds a **fixed number of values** of the **same type**. In Java, arrays are **objects** stored in **heap memory**.

### 🏗️ Memory Structure

```
Array in Memory:
┌─────┬─────┬─────┬─────┬─────┐
│ [0] │ [1] │ [2] │ [3] │ [4] │
│ 10  │ 20  │ 30  │ 40  │ 50  │
└─────┴─────┴─────┴─────┴─────┘
  ↑                           ↑
Base Address              Last Element
```

### 🔧 Array Declaration & Initialization

#### 📊 Declaration Methods

| **Method**                   | **Syntax**                        | **Description**                   |
| ---------------------------- | --------------------------------- | --------------------------------- |
| Declaration + Allocation     | `int[] arr = new int[5];`         | Creates array with default values |
| Declaration + Initialization | `int[] arr = {10, 20, 30};`       | Directly initializes array        |
| Alternative Syntax           | `int arr[] = new int[]{1, 2, 3};` | C-style declaration               |

```java
int[] marks = new int[5]; // [0, 0, 0, 0, 0]
int[] scores = {95, 87, 92, 78, 88};
int[] values = new int[]{1, 2, 3, 4, 5};
```

#### 🎯 Default Values by Data Type

| **Data Type** | **Default Value** | **Example**       |
| ------------- | ----------------- | ----------------- |
| `int`         | 0                 | `[0, 0, 0]`       |
| `double`      | 0.0               | `[0.0, 0.0, 0.0]` |
| `boolean`     | false             | `[false, false]`  |
| `String`      | null              | `[null, null]`    |

### 🔍 Accessing Array Elements

```java
int[] scores = {95, 87, 92, 78, 88};
System.out.println(scores[0]);  // 95
System.out.println(scores[4]);  // 88

scores[2] = 100;  // Change 92 to 100

System.out.println(scores.length);  // 5
```

> 💡 Use `.length` (not `.length()`) for arrays!

---

## ⚙️ Part 2: Core Array Operations

### 🔄 1. Traversal

```java
int[] numbers = {10, 20, 30, 40, 50};

// Traditional
for (int i = 0; i < numbers.length; i++) {
    System.out.print(numbers[i] + " ");
}

// Enhanced (for-each)
for (int num : numbers) {
    System.out.print(num + " ");
}
```

### ➕ 2. Insertion

> ⚠️ Arrays have **fixed size**, so insertion requires **manual shifting**.

```java
public static void insertAt(int[] arr, int pos, int value, int size) {
    for (int i = size - 1; i > pos; i--) {
        arr[i] = arr[i - 1];
    }
    arr[pos] = value;
}

// Example:
int[] arr = {10, 20, 30, 40, 0};
insertAt(arr, 2, 25, 4);
// Result: [10, 20, 25, 30, 40]
```

#### ➕ Insertion Complexity

| **Position** | **Time Complexity** | **Reason**            |
| ------------ | ------------------- | --------------------- |
| At End       | O(1)                | No shifting           |
| At Beginning | O(n)                | Shift all             |
| At Middle    | O(n)                | Shift half on average |

---

### ❌ 3. Deletion

```java
public static int deleteAt(int[] arr, int pos, int size) {
    for (int i = pos; i < size - 1; i++) {
        arr[i] = arr[i + 1];
    }
    return size - 1;
}
```

---

### 🔍 4. Searching

#### Linear Search

```java
public static int linearSearch(int[] arr, int target) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == target) return i;
    }
    return -1;
}
```

#### Binary Search (Sorted Only)

```java
public static int binarySearch(int[] arr, int target) {
    int left = 0, right = arr.length - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == target) return mid;
        else if (arr[mid] < target) left = mid + 1;
        else right = mid - 1;
    }
    return -1;
}
```

---

### ✏️ 5. Update

```java
int[] grades = {85, 92, 78, 96, 88};

grades[2] = 95; // Update single

for (int i = 0; i < grades.length; i++) {
    grades[i] += 5; // Bonus
}
```

---

### 📊 Operation Complexity Summary

| **Operation**   | **Time** | **Space** | **Notes**             |
| --------------- | -------- | --------- | --------------------- |
| Access          | O(1)     | O(1)      | Direct index          |
| Insert (end)    | O(1)     | O(1)      | If space is available |
| Insert (middle) | O(n)     | O(1)      | Requires shifting     |
| Delete          | O(n)     | O(1)      | Requires shifting     |
| Linear Search   | O(n)     | O(1)      | Worst-case            |
| Binary Search   | O(log n) | O(1)      | Sorted only           |

---

## 🧩 Part 3: Multidimensional & Jagged Arrays

### 🧮 2D Arrays

```java
int[][] matrix = new int[3][4];
int[][] scores = {
    {85, 92, 78, 96},
    {88, 91, 85, 89},
    {90, 87, 93, 94}
};
```

### 🪢 Jagged Arrays

```java
int[][] jagged = new int[3][];
jagged[0] = new int[4];
jagged[1] = new int[2];
jagged[2] = new int[5];
```

---

## 📦 Part 4: Java Utility Methods

### 🛠️ Arrays Class Methods

```java
import java.util.Arrays;

int[] numbers = {5, 3, 1, 4, 2};

Arrays.sort(numbers);
System.out.println(Arrays.toString(numbers)); // [1, 2, 3, 4, 5]
Arrays.fill(numbers, 0);
```

---

## 📉 Part 5: Time & Space Complexity

| **Operation**    | **Time** | **Space** |
| ---------------- | -------- | --------- |
| Access by index  | O(1)     | O(1)      |
| Insert at middle | O(n)     | O(1)      |
| Delete at middle | O(n)     | O(1)      |
| Linear search    | O(n)     | O(1)      |
| Binary search    | O(log n) | O(1)      |

---

## 🚨 Part 6: Common Pitfalls

### 1. ArrayIndexOutOfBounds

```java
int[] arr = new int[3];
arr[3] = 10; // ❌ Error

if (index >= 0 && index < arr.length) {
    arr[index] = value; // ✅
}
```

---

## 🆚 Part 7: Array vs ArrayList

| Feature     | Array              | ArrayList       |
| ----------- | ------------------ | --------------- |
| Size        | Fixed              | Dynamic         |
| Data Type   | Primitives/Objects | Objects only    |
| Performance | Fast               | Slower (boxing) |
| Flexibility | Low                | High            |

---

## 🧠 Part 8: Dynamic Arrays (ArrayList Internal Working)

```java
ArrayList<Integer> list = new ArrayList<>();
// Internally:
// - Initial capacity: 10
// - Grows by 1.5x when full
```

| **Current Size** | **New Size** | **Growth Factor** |
| ---------------- | ------------ | ----------------- |
| 10               | 15           | 1.5x              |
| 15               | 22           | 1.5x              |
| 22               | 33           | 1.5x              |

> ⚠️ Frequent resizing = O(n)

---

## 🛠️ Part 9: Practical Applications

```java
int[][] image = new int[1920][1080]; // Image matrix
String[] months = {"Jan", "Feb", "Mar"};
Arrays.sort(data); // For algorithms
```

---

## 📚 Part 10: Interview Tips

```java
public static int safeAccess(int[] arr, int index) {
    if (arr == null || index < 0 || index >= arr.length) return -1;
    return arr[index];
}
```

### Interview Patterns

| Pattern            | Examples         | Technique           |
| ------------------ | ---------------- | ------------------- |
| Two Pointers       | Two Sum          | Start & end index   |
| Sliding Window     | Max Subarray     | Move window         |
| Binary Search      | Sorted Arrays    | Divide & conquer    |
| Kadane's Algorithm | Max Subarray Sum | Dynamic programming |

---

## ✅ Final Mastery Checklist

| Topic                   | Status | Key Points                           |
| ----------------------- | ------ | ------------------------------------ |
| Array Basics            | ✅      | Fixed size, zero-based index         |
| Core Operations         | ✅      | CRUD, traversal, search              |
| Multidimensional Arrays | ✅      | 2D and jagged arrays                 |
| Java Utilities          | ✅      | Arrays class methods                 |
| Complexity Analysis     | ✅      | Time/Space complexity                |
| Error Handling          | ✅      | Boundary checks, null checks         |
| Array vs ArrayList      | ✅      | Static vs dynamic arrays             |
| Practical Applications  | ✅      | Real-world & algorithmic use         |
| Interview Preparation   | ✅      | Patterns, techniques, best practices |

---


