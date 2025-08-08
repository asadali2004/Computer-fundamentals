# � Arrays in Java — Complete Mastery Guide

> **🎯 Master Linear Data Structures**: From fundamental concepts ### ➕ 2. Array Insertion

**⚠️ Limitation**: Arrays have **fixed size**, so insertion requires **manual shifting**.

```java
// 🔧 Insert element at specific position
public static void insertAt(int[] arr, int pos, int value, int size) {
    // Shift elements to the right
    for (int i = size - 1; i > pos; i--) {
        arr[i] = ar## 🧠 Part 8: Dynamic Arrays (ArrayList Internal Working)

### 🔄 How ArrayList Handles Growth

```java
// 🎯 ArrayList Internal Process
ArrayList<Integer> list = new ArrayList<>(); // Initial capacity: 10

// When array gets full:
// 1. Create new array (1.5x current size)
// 2. Copy all elements to new array
// 3. Add new element
// 4. Update reference to new array
```

#### 📊 Growth Strategy

| **Current Size** | **New Size** | **Growth Factor** |
|------------------|--------------|-------------------|
| 10 | 15 | 1.5x |
| 15 | 22 | 1.5x |
| 22 | 33 | 1.5x |

> **⚠️ Performance Impact**: Frequent resizing can cause O(n) operations occasionally.

---
    }
    // Insert new value
    arr[pos] = value;
}

// Example usage:
int[] arr = {10, 20, 30, 40, 0}; // Extra space for insertion
insertAt(arr, 2, 25, 4);
// Result: [10, 20, 25, 30, 40]
```

#### ➕ Insertion Complexity

| **Position** | **Time Complexity** | **Reason** |
|--------------|-------------------|------------|
| **At End** | O(1) | No shifting required |
| **At Beginning** | O(n) | Shift all elements |
| **At Middle** | O(n) | Shift half elements on average |

---array operations and interview preparation

---

## 📋 Learning Roadmap

| **Section** | **Topic** | **Key Focus** |
|-------------|-----------|---------------|
| 🔰 **Fundamentals** | Array Basics | Declaration, initialization, access |
| ⚙️ **Operations** | Core Array Operations | Insertion, deletion, searching, traversal |
| � **Multidimensional** | 2D & Jagged Arrays | Matrix operations and complex structures |
| 📦 **Java Utilities** | Arrays Class Methods | Built-in sorting, searching, copying |
| ⏱️ **Complexity** | Performance Analysis | Time and space complexity |
| ⚠️ **Pitfalls** | Common Errors | Exception handling and best practices |
| 🆚 **Comparisons** | Array vs ArrayList | Static vs dynamic arrays |
| 🧠 **Interview Prep** | Problem Patterns | Common questions and optimization techniques |

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

| **Method** | **Syntax** | **Description** |
|------------|------------|-----------------|
| **Declaration + Allocation** | `int[] arr = new int[5];` | Creates array with default values |
| **Declaration + Initialization** | `int[] arr = {10, 20, 30};` | Creates and initializes in one step |
| **Alternative Syntax** | `int arr[] = new int[]{1, 2, 3};` | C-style declaration |

```java
// 🎯 Various initialization methods
int[] marks = new int[5];           // [0, 0, 0, 0, 0]
int[] scores = {95, 87, 92, 78, 88}; // Direct initialization
int[] values = new int[]{1, 2, 3, 4, 5}; // Explicit initialization
```

#### 🎯 Default Values by Data Type

| **Data Type** | **Default Value** | **Example** |
|---------------|-------------------|-------------|
| `int` | 0 | `[0, 0, 0]` |
| `double` | 0.0 | `[0.0, 0.0, 0.0]` |
| `boolean` | false | `[false, false, false]` |
| `String` (Object) | null | `[null, null, null]` |

### 🔍 Accessing Array Elements

**🎯 Key Concept**: Java arrays are **zero-indexed** (first element is at index 0).

```java
int[] scores = {95, 87, 92, 78, 88};

// ✅ Accessing elements
System.out.println(scores[0]);  // 95 (first element)
System.out.println(scores[4]);  // 88 (last element)

// ✅ Modifying elements
scores[2] = 100;  // Changes 92 to 100

// ✅ Getting array length
System.out.println(scores.length);  // 5 (NO parentheses!)
```

> **💡 Important**: Use `.length` (not `.length()`) for arrays!

---
## ⚙️ Part 2: Core Array Operations
### 🔄 1. Array Traversal

**🎯 Two Main Methods**: Traditional for-loop and Enhanced for-loop

```java
int[] numbers = {10, 20, 30, 40, 50};

// 📊 Method 1: Traditional for-loop (with index access)
for (int i = 0; i < numbers.length; i++) {
    System.out.print(numbers[i] + " ");
}

// 🎯 Method 2: Enhanced for-loop (for-each) - cleaner syntax
for (int num : numbers) {
    System.out.print(num + " ");
}
```

#### 📊 Traversal Comparison

| **Method** | **Pros** | **Cons** | **Use When** |
|------------|----------|----------|--------------|
| **Traditional for-loop** | Index access, modification possible | More verbose | Need index or modifying array |
| **Enhanced for-loop** | Clean, readable code | No index access | Just reading values |

---
✅ 2. Insertion
You can’t "insert" in the middle unless you shift elements manually.

java
Copy
Edit
// Insert at index 2
int[] arr = {10, 20, 30, 40};
for (int i = 4 - 1; i > 2; i--) {
    arr[i] = arr[i - 1];
}
arr[2] = 25;
### ❌ 3. Array Deletion

**🎯 Strategy**: Shift elements left after deletion point.

```java
// 🗑️ Delete element at specific position
public static int deleteAt(int[] arr, int pos, int size) {
    // Shift elements to the left
    for (int i = pos; i < size - 1; i++) {
        arr[i] = arr[i + 1];
    }
    return size - 1; // Return new size
}

// Example usage:
int[] arr = {10, 20, 30, 40, 50};
int newSize = deleteAt(arr, 2, 5);
// Result: [10, 20, 40, 50] with newSize = 4
```

---
### 🔍 4. Array Searching

#### 📖 Linear Search (Unsorted Arrays)

```java
// 🔍 Linear Search Implementation
public static int linearSearch(int[] arr, int target) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == target) {
            return i; // Return index if found
        }
    }
    return -1; // Return -1 if not found
}

// Time Complexity: O(n)
// Space Complexity: O(1)
```

#### 🎯 Binary Search (Sorted Arrays Only)

```java
// ⚡ Binary Search Implementation
public static int binarySearch(int[] arr, int target) {
    int left = 0;
    int right = arr.length - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2; // Avoid overflow
        
        if (arr[mid] == target) {
            return mid; // Found target
        } else if (arr[mid] < target) {
            left = mid + 1; // Search right half
        } else {
            right = mid - 1; // Search left half
        }
    }
    return -1; // Target not found
}

// Time Complexity: O(log n)
// Space Complexity: O(1)
```

#### 🔍 Search Algorithm Comparison

| **Algorithm** | **Time Complexity** | **Prerequisite** | **Best For** |
|---------------|-------------------|------------------|--------------|
| **Linear Search** | O(n) | None | Small/unsorted arrays |
| **Binary Search** | O(log n) | **Sorted array** | Large sorted arrays |

---
### ✏️ 5. Array Update

```java
// 🔄 Simple element update
int[] grades = {85, 92, 78, 96, 88};

// Update single element
grades[2] = 95; // Change 78 to 95

// Update multiple elements
for (int i = 0; i < grades.length; i++) {
    grades[i] += 5; // Add 5 bonus points to all grades
}
```

### 📊 Operations Complexity Summary

| **Operation** | **Time Complexity** | **Space Complexity** | **Notes** |
|---------------|-------------------|-------------------|-----------|
| **Access** | O(1) | O(1) | Direct index access |
| **Traversal** | O(n) | O(1) | Visit all elements |
| **Insert (End)** | O(1) | O(1) | If space available |
| **Insert (Middle)** | O(n) | O(1) | Requires shifting |
| **Delete** | O(n) | O(1) | Requires shifting |
| **Linear Search** | O(n) | O(1) | Worst case: check all |
| **Binary Search** | O(log n) | O(1) | Only on sorted arrays |

---
## 🔍 Part 3: Multidimensional & Jagged Arrays

### 📊 1. 2D Arrays (Matrices)

**🎯 Concept**: Array of arrays - think of it as a **table** with rows and columns.

```java
// 📋 2D Array Declaration and Initialization
int[][] matrix = new int[3][4]; // 3 rows, 4 columns

// 🎯 Initialize with values
int[][] scores = {
    {85, 92, 78, 96},
    {88, 91, 85, 89},
    {90, 87, 93, 94}
};

// 🔄 Traversal using nested loops
for (int i = 0; i < matrix.length; i++) {        // rows
    for (int j = 0; j < matrix[i].length; j++) {  // columns
        matrix[i][j] = i + j;
        System.out.print(matrix[i][j] + " ");
    }
    System.out.println(); // New line after each row
}
```

#### 🔍 2D Array Memory Visualization

```
matrix[3][4] in memory:
[0] [1] [2] [3]
[1] [2] [3] [4]  
[2] [3] [4] [5]
```

---
### 🔀 2. Jagged Arrays

**🎯 Concept**: Arrays where **each row can have different sizes** - like a ragged/jagged edge.

```java
// 🔧 Jagged Array Declaration
int[][] jagged = new int[3][]; // 3 rows, columns vary

// 📏 Different row sizes
jagged[0] = new int[4];  // Row 0: 4 elements
jagged[1] = new int[2];  // Row 1: 2 elements  
jagged[2] = new int[5];  // Row 2: 5 elements

// 🎯 Initialize with values
int[][] studentGrades = {
    {85, 92, 78},           // Student 1: 3 subjects
    {88, 91},               // Student 2: 2 subjects
    {90, 87, 93, 94, 89}    // Student 3: 5 subjects
};

// 🔄 Traversal - must check each row's length
for (int i = 0; i < studentGrades.length; i++) {
    System.out.print("Student " + (i+1) + ": ");
    for (int j = 0; j < studentGrades[i].length; j++) {
        System.out.print(studentGrades[i][j] + " ");
    }
    System.out.println();
}
```

#### 🔍 Jagged vs Regular Array Comparison

| **Type** | **Row Sizes** | **Memory Usage** | **Use Case** |
|----------|---------------|------------------|--------------|
| **Regular 2D** | All same | Fixed, may waste space | Matrices, grids |
| **Jagged** | Can vary | Optimized, no waste | Real-world data |

---
## 📦 Part 4: Java Utility Methods (`Arrays` Class)

### 🛠️ Essential Array Utilities

**📋 Import Required**: `import java.util.Arrays;`

```java
import java.util.Arrays;

int[] numbers = {5, 3, 1, 4, 2};

// 🔄 1. Sorting Array
Arrays.sort(numbers);
System.out.println(Arrays.toString(numbers)); // [1, 2, 3, 4, 5]

// 🔍 2. Convert Array to String (for printing)
String arrayStr = Arrays.toString(numbers);
System.out.println(arrayStr); // [1, 2, 3, 4, 5]

// 🎯 3. Binary Search (only on sorted arrays)
int index = Arrays.binarySearch(numbers, 4);
System.out.println("Found 4 at index: " + index); // Found 4 at index: 3

// 📋 4. Copy Array
int[] copy1 = Arrays.copyOf(numbers, numbers.length);    // Exact copy
int[] copy2 = Arrays.copyOf(numbers, 10);               // Copy with new size
int[] copy3 = Arrays.copyOfRange(numbers, 1, 4);        // Copy portion [1,4)

// 🔄 5. Fill Array with value
int[] fillArray = new int[5];
Arrays.fill(fillArray, 99);
System.out.println(Arrays.toString(fillArray)); // [99, 99, 99, 99, 99]

// ⚖️ 6. Compare Arrays
int[] arr1 = {1, 2, 3};
int[] arr2 = {1, 2, 3};
boolean isEqual = Arrays.equals(arr1, arr2);
System.out.println("Arrays equal: " + isEqual); // true
```

### 📊 Arrays Class Methods Summary

| **Method** | **Purpose** | **Example** | **Time Complexity** |
|------------|-------------|-------------|-------------------|
| `sort(arr)` | Sort array | `Arrays.sort(arr)` | O(n log n) |
| `toString(arr)` | Array to string | `Arrays.toString(arr)` | O(n) |
| `binarySearch(arr, key)` | Search in sorted array | `Arrays.binarySearch(arr, 5)` | O(log n) |
| `copyOf(arr, length)` | Copy array | `Arrays.copyOf(arr, 10)` | O(n) |
| `fill(arr, value)` | Fill with value | `Arrays.fill(arr, 0)` | O(n) |
| `equals(arr1, arr2)` | Compare arrays | `Arrays.equals(arr1, arr2)` | O(n) |

---
## ⚙️ Part 5: Time & Space Complexity Analysis
### 📊 Array Operations Complexity

| **Operation** | **Time Complexity** | **Space Complexity** | **Explanation** |
|---------------|-------------------|-------------------|-----------------|
| **Access by Index** | O(1) | O(1) | Direct memory access |
| **Insert at End** | O(1) | O(1) | No shifting required |
| **Insert at Middle** | O(n) | O(1) | Shift n/2 elements on average |
| **Delete at Middle** | O(n) | O(1) | Shift elements after deletion |
| **Linear Search** | O(n) | O(1) | May need to check all elements |
| **Binary Search** | O(log n) | O(1) | Only for sorted arrays |

> **💡 Key Insight**: Arrays excel at **random access** but struggle with **dynamic operations**.

---

## ⚠️ Part 6: Common Errors & Pitfalls

### 🚨 1. ArrayIndexOutOfBoundsException

```java
// ❌ Common mistake
int[] arr = new int[3]; // Valid indices: 0, 1, 2
arr[3] = 10;  // ❌ Error! Index 3 doesn't exist

// ✅ Correct way
if (index >= 0 && index < arr.length) {
    arr[index] = value; // Safe access
}
```

### 🚨 2. Using `.length()` instead of `.length`

```java
int[] numbers = {1, 2, 3, 4, 5};

// ❌ Wrong (this is for Strings)
int size = numbers.length();  // ❌ Compilation error!

// ✅ Correct (for arrays)
int size = numbers.length;    // ✅ Correct
```

---
## 📈 Part 7: Array vs ArrayList Comparison

| **Feature** | **Array** | **ArrayList** |
|-------------|-----------|---------------|
| **Size** | ✅ Fixed size | ✅ Dynamic (resizable) |
| **Data Types** | ✅ Primitives + Objects | ❌ Objects only |
| **Memory** | ✅ Efficient | ❌ Extra overhead |
| **Syntax** | `int[]` | `ArrayList<Integer>` |
| **Methods** | ❌ Limited | ✅ Rich API |
| **Performance** | ✅ Faster access | ❌ Slower (boxing/unboxing) |
| **Flexibility** | ❌ Low | ✅ High |

### 🔍 When to Use Which?

```java
// ✅ Use Array when:
// - Fixed size known in advance
// - Need maximum performance
// - Working with primitives
int[] scores = new int[100]; // Game scores for 100 levels

// ✅ Use ArrayList when:
// - Size varies during runtime
// - Need dynamic operations (add/remove)
// - Convenience methods important
ArrayList<String> names = new ArrayList<>(); // User list
```

---

🧠 PART 8: DYNAMIC ARRAYS (ArrayList Internal Working)
When the array inside ArrayList gets full, it:

Creates a new array of 1.5x or 2x size

Copies all elements to the new array

Adds the new element

That’s why frequent resizing → O(n)

## 🛠️ Part 9: Practical Applications

### 🎯 Real-World Use Cases

```java
// 📊 1. Matrix Operations (Image Processing)
int[][] image = new int[1920][1080]; // HD image pixels

// 🔍 2. Lookup Tables (Hashing)
String[] months = {"Jan", "Feb", "Mar", ...}; // O(1) access

// 📈 3. Sorting Algorithms
int[] data = {64, 34, 25, 12, 22, 11, 90};
Arrays.sort(data); // Built on array operations

// 🎮 4. Game Development
int[] playerScores = new int[4]; // Multiplayer game
boolean[][] gameBoard = new boolean[8][8]; // Chess board

// 📚 5. Data Structures Foundation
// - Stacks, Queues, Heaps use arrays internally
// - Hash tables use arrays for buckets
// - Dynamic programming tables
```

---

## 📚 Part 10: Interview Tips & Best Practices

### 🎯 Essential Interview Points

```java
// ✅ Always check boundaries
public static int safeAccess(int[] arr, int index) {
    if (arr == null || index < 0 || index >= arr.length) {
        return -1; // or throw exception
    }
    return arr[index];
}

// ✅ Handle edge cases
public static void processArray(int[] arr) {
    if (arr == null || arr.length == 0) {
        System.out.println("Empty array");
        return;
    }
    // Process array...
}
```

### 🧠 Common Interview Patterns

| **Pattern** | **Example Problems** | **Key Technique** |
|-------------|---------------------|-------------------|
| **Two Pointers** | Two Sum, Palindrome | Start/End pointers |
| **Sliding Window** | Max subarray | Moving window |
| **Binary Search** | Search in sorted | Divide & conquer |
| **Kadane's Algorithm** | Maximum subarray sum | Dynamic programming |

---

## ✅ Final Mastery Checklist

| **Topic** | **Status** | **Key Points** |
|-----------|------------|----------------|
| **Array Basics & Declaration** | ✅ | Fixed size, zero-indexed, contiguous memory |
| **Core Operations (CRUD)** | ✅ | Access O(1), Insert/Delete O(n), Search O(n)/O(log n) |
| **Multidimensional Arrays** | ✅ | 2D arrays, jagged arrays, nested loops |
| **Java Utilities** | ✅ | Arrays class methods, sorting, searching |
| **Complexity Analysis** | ✅ | Time/Space complexity for all operations |
| **Error Handling** | ✅ | Boundary checks, null handling |
| **Array vs ArrayList** | ✅ | Fixed vs dynamic, performance trade-offs |
| **Practical Applications** | ✅ | Real-world use cases, algorithm foundations |
| **Interview Preparation** | ✅ | Common patterns, best practices |

---

## 🎉 Congratulations!

You've now mastered **Arrays in Java**! You understand:
- ✅ **Core concepts** and memory model
- ✅ **All essential operations** with complexity analysis
- ✅ **Advanced topics** like multidimensional arrays
- ✅ **Java utilities** and best practices
- ✅ **Interview preparation** and real-world applications

**🚀 Next Steps**: Practice array-based problems on LeetCode, HackerRank, or similar platforms to solidify your understanding!