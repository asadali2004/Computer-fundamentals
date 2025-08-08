
# 📘 HASH TABLES / HASH MAPS — From Basics to Advanced Mastery (Java + DSA Theory)

---

## 🔰 PART 1: WHAT IS A HASH TABLE?

---

### ✅ Definition:

A **Hash Table** is a **data structure** that stores data in **key-value pairs** and allows for **fast lookup**, **insertion**, and **deletion**, ideally in **O(1)** time.

---

### ✅ Real-Life Analogy:

Imagine a **library catalog** where:

* The **key** = book title
* The **value** = location on the shelf

You enter the title, and it gives you the book’s exact spot — instantly.

---

### ✅ Visual Structure:

```
Index:   0     1     2     3     4     5
         ↓     ↓     ↓     ↓     ↓     ↓
        null  (K1,V1) null (K2,V2)(K3,V3) null
```

Keys are placed at **hashed indexes** inside an internal array.

---

## 🔐 Part 2: The Heart of Hash Tables — Hash Functions

### 🔧 What is a Hash Function?

A **hash function** converts a key (e.g., string, int) into an **index** in the internal array.

```java
index = hash(key) % table_size;
```

### 🎯 Properties of a Good Hash Function

| **Property** | **Description** | **Why Important** |
|--------------|-----------------|-------------------|
| 🎲 **Deterministic** | Same input → same output | Consistency in storage/retrieval |
| 📊 **Uniform Distribution** | Spread keys evenly across array | Minimize collisions |
| ⚡ **Fast Computation** | Quick to calculate | Maintain O(1) performance |
| 🎯 **Minimize Collisions** | Different keys → different indices | Avoid performance degradation |

### 🧮 Hash Function Example

```java
// Simple hash function example
public int hash(String key) {
    int hash = 0;
    for (int i = 0; i < key.length(); i++) {
        hash = (hash * 31 + key.charAt(i)) % tableSize;
    }
    return hash;
}

// Example usage:
hash("Apple") = 40123
index = 40123 % 10 = 3  // Maps to index 3
```

---

## ⚠️ PART 3: COLLISIONS AND RESOLUTION

---

### ✅ What is a Collision?

When two different keys produce the **same index**, it’s called a **collision**.

E.g.,
`hash("cat") % 5 → 2`
`hash("dog") % 5 → 2`
Both map to index 2

---

### ✅ Collision Resolution Techniques:

---

#### 🔹 1. **Chaining (Used in Java HashMap)**

* Use a **linked list (or array list)** at each index
* All values with same hash are stored in a list

```plaintext
Index 3: → (Key1, Val1) → (Key2, Val2)
```

✅ Easy to implement
❌ Search becomes O(n) if too many collisions

---

#### 🔹 2. **Open Addressing**

* All elements stored in the main array
* On collision, search for the next empty slot

##### Types:

* **Linear Probing**: Next index → (i + 1) % size
* **Quadratic Probing**: (i + 1²), (i + 2²), ...
* **Double Hashing**: Use second hash function

✅ Space-efficient
❌ Clustering problem

---

## ⚙️ Part 4: Hash Table Operations

### 🔧 Core Operations Overview

| **Operation** | **Average Time** | **Worst Case** | **Description** |
|---------------|------------------|----------------|-----------------|
| **Insert** | O(1) | O(n) | Add key-value pair |
| **Search** | O(1) | O(n) | Find value by key |
| **Delete** | O(1) | O(n) | Remove key-value pair |

### 1️⃣ Insert Operation

```java
// Insert algorithm
1. hash = hash(key) % capacity
2. if (table[hash] is empty):
       table[hash] = new Entry(key, value)
   else:
       // Handle collision (chaining or probing)
       resolve_collision(hash, key, value)
```

**⏱️ Time Complexity**: 
- **Average**: O(1) - Direct placement
- **Worst**: O(n) - All keys hash to same index

### 2️⃣ Search Operation

```java
// Search algorithm
1. hash = hash(key) % capacity
2. if (table[hash].key == target_key):
       return table[hash].value
   else:
       // Follow collision resolution method
       return search_in_collision_chain(hash, target_key)
```

**🔍 Process**:
1. Compute hash of the key
2. Go to calculated index
3. If chaining: traverse linked list
4. If open addressing: probe sequence

### 3️⃣ Delete Operation

**📋 Strategy varies by collision resolution**:

| **Resolution Method** | **Deletion Process** |
|----------------------|---------------------|
| **Chaining** | Remove from linked list at index |
| **Open Addressing** | Mark as deleted (special marker/tombstone) |

> **⚠️ Important**: In open addressing, actual deletion can break probe sequences, so we use "tombstone" markers.

---

## 🧮 Part 5: Load Factor & Rehashing

### 📊 Understanding Load Factor (α)

```
α = number of elements / table size
```

**🎯 Example**: If we have 15 elements in a table of size 20:
```
Load Factor = 15/20 = 0.75 (75% full)
```

### 📈 Load Factor Impact

| **Load Factor Range** | **Performance** | **Collision Rate** | **Action Needed** |
|----------------------|-----------------|-------------------|-------------------|
| **0.0 - 0.5** | 🟢 Excellent | Very Low | Optimal performance |
| **0.5 - 0.75** | 🟡 Good | Moderate | Monitor closely |
| **0.75 - 1.0** | 🟠 Degrading | High | **Rehashing recommended** |
| **> 1.0** | 🔴 Poor | Very High | **Immediate rehashing required** |

### 🔄 Rehashing Process

When load factor exceeds threshold (typically **0.75**):

#### 📋 Rehashing Steps:
1. **📏 Create new table**: Usually **double the size** (e.g., 16 → 32)
2. **🔄 Recompute hashes**: All existing keys get new hash values
3. **📦 Re-insert elements**: Transfer all key-value pairs to new table
4. **🗑️ Discard old table**: Free up old array memory

```java
// Simplified rehashing pseudocode
if (loadFactor > 0.75) {
    oldTable = currentTable;
    currentTable = new Table(oldTable.size * 2);
    
    for (entry : oldTable) {
        if (entry != null) {
            newHash = hash(entry.key) % currentTable.size;
            insert(currentTable, newHash, entry);
        }
    }
}
```

### ⏱️ Rehashing Cost Analysis

| **Aspect** | **Cost** | **Amortization** |
|------------|----------|------------------|
| **Individual rehashing** | O(n) - expensive | Rare occurrence |
| **Average over many operations** | O(1) | Amortized constant time |

> **💡 Key Insight**: Though rehashing is costly (O(n)), it happens infrequently, making the **amortized** cost O(1) per operation.

---

## ☕ Part 6: Hash Tables in Java (HashMap)

### 🚀 HashMap Declaration & Basic Operations

```java
// Creating and using HashMap
Map<String, Integer> map = new HashMap<>();

// Basic operations
map.put("apple", 2);           // Insert
map.get("apple");              // Returns 2 (Search)
map.remove("apple");           // Delete
map.containsKey("apple");      // Returns false
map.containsValue(2);          // Check if value exists
map.size();                    // Get number of elements
map.isEmpty();                 // Check if empty
```

### 🏗️ HashMap Internal Architecture

#### 📋 Behind the Scenes:

| **Java Version** | **Internal Structure** | **Collision Handling** |
|------------------|------------------------|------------------------|
| **Java 7 & earlier** | Array of `Entry<K,V>` | LinkedList at each bucket |
| **Java 8+** | Array of `Node<K,V>` | LinkedList → **Balanced BST** (when chain > 8) |

```java
// Simplified internal structure
class HashMap<K,V> {
    Node<K,V>[] table;        // Main array
    int size;                 // Number of elements
    int threshold;            // Rehashing trigger
    float loadFactor = 0.75f; // Default load factor
}
```

### 🎯 Important HashMap Behaviors

| **Behavior** | **Details** | **Example/Note** |
|--------------|-------------|------------------|
| **Null Keys & Values** | ✅ Allows 1 null key, multiple null values | `map.put(null, "value")` |
| **Thread Safety** | ❌ Not thread-safe | Use `ConcurrentHashMap` for concurrency |
| **Ordering** | ❌ No insertion order maintained | Use `LinkedHashMap` for order |
| **Sorted Keys** | ❌ No natural sorting | Use `TreeMap` for sorted keys |
| **Initial Capacity** | Default: 16 | Can specify: `new HashMap<>(32)` |
| **Load Factor** | Default: 0.75 | Can customize: `new HashMap<>(16, 0.8f)` |

### 🔧 HashMap Performance Optimizations (Java 8+)

#### 🌳 Tree-ification Process:
```
LinkedList → Tree conversion happens when:
1. Bucket chain length > 8 (TREEIFY_THRESHOLD)
2. Total table size ≥ 64 (MIN_TREEIFY_CAPACITY)

Tree → LinkedList conversion when:
- Chain length < 6 (UNTREEIFY_THRESHOLD)
```

**🎯 Result**: Even with poor hash functions, worst-case search becomes **O(log n)** instead of **O(n)**.

---

## 🧩 Part 7: Real-World Applications of Hash Tables

### 🌍 Where Hash Tables Shine

| **Application Area** | **Use Case** | **Example** | **Why Hash Tables?** |
|---------------------|--------------|-------------|----------------------|
| 🔍 **Lookup Tables** | Store information for fast access | Phone directory, DNS cache | O(1) lookup time |
| 💾 **Caching** | Memoization, LRU cache implementation | Web browser cache, CPU cache | Fast data retrieval |
| 📊 **Counting & Frequency** | Count occurrences, find duplicates | Word frequency, vote counting | Efficient counting operations |
| 🕸️ **Graph Problems** | Adjacency list representation | `Map<Node, List<Node>>` | Dynamic graph structure |
| 🔢 **Set Operations** | Union, intersection, difference | Database joins, data deduplication | Fast membership testing |
| 🗃️ **Database Indexing** | Primary keys, foreign key lookups | SQL database indexes | Constant-time record access |
| 📝 **Compiler Design** | Symbol tables, variable storage | Variable scope management | Quick symbol resolution |
| 🌐 **JSON Parsing** | Key-value parsing of objects | API response parsing | Dynamic object handling |

### 💡 Programming Interview Applications

```java
// Example: Two Sum Problem
public int[] twoSum(int[] nums, int target) {
    Map<Integer, Integer> map = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
        int complement = target - nums[i];
        if (map.containsKey(complement)) {
            return new int[]{map.get(complement), i};
        }
        map.put(nums[i], i);
    }
    return new int[]{};
}
```

---

## 📊 Part 8: Time & Space Complexity Analysis

### ⏱️ Time Complexity Breakdown

| **Operation** | **Average Case** | **Worst Case** | **Best Case** | **Real-World Performance** |
|---------------|------------------|----------------|---------------|---------------------------|
| **🔍 Search** | **O(1)** | O(n) | O(1) | Usually O(1) with good hash function |
| **➕ Insert** | **O(1)** | O(n) | O(1) | Usually O(1), O(n) during rehashing |
| **❌ Delete** | **O(1)** | O(n) | O(1) | Usually O(1) with good hash function |

### 💾 Space Complexity

| **Component** | **Space Usage** | **Description** |
|---------------|-----------------|-----------------|
| **Main Array** | O(m) | Where m = table capacity |
| **Stored Elements** | O(n) | Where n = number of elements |
| **Total Space** | **O(n + m)** | Usually m ≈ n/α, so **O(n)** |

### 🎯 Why Worst Case Rarely Happens

| **Protection Mechanism** | **How It Helps** | **Result** |
|--------------------------|------------------|------------|
| 🔧 **Good Hash Functions** | Uniform distribution of keys | Minimizes collisions |
| 🔄 **Automatic Rehashing** | Maintains low load factor | Prevents overcrowding |
| 🌳 **Tree Fallback (Java 8+)** | Converts long chains to balanced trees | O(log n) instead of O(n) |
| 📊 **Load Factor Management** | Triggers expansion when needed | Maintains performance |

### 📈 Performance Comparison

```java
// Performance comparison of different data structures
Operation     | Array | LinkedList | HashMap | TreeMap
------------- | ----- | ---------- | ------- | -------
Search        | O(n)  | O(n)       | O(1)*   | O(log n)
Insert        | O(n)  | O(1)       | O(1)*   | O(log n)
Delete        | O(n)  | O(n)       | O(1)*   | O(log n)
Space         | O(n)  | O(n)       | O(n)    | O(n)

* Average case performance
```

---

## ⚠️ Part 9: Common Pitfalls & Best Practices

### 🚨 Common Mistakes to Avoid

| **Pitfall** | **Problem** | **Solution** | **Example** |
|-------------|-------------|--------------|-------------|
| 🔧 **Poor Hash Function** | Many collisions → O(n) performance | Use proven hash algorithms | Use built-in `hashCode()` or proven libraries |
| 🔄 **Mutable Keys** | Changing key after insertion | Use immutable objects as keys | Use `String`, `Integer`, or custom immutable classes |
| 🔍 **Null Handling** | `NullPointerException` in operations | Always check for null | `if (key != null) map.get(key)` |
| ⚖️ **equals() & hashCode()** | Inconsistent object equality | Override both methods correctly | If `a.equals(b)`, then `a.hashCode() == b.hashCode()` |

### 📋 Best Practices Checklist

#### ✅ Hash Function Design
```java
// Good hashCode() implementation
@Override
public int hashCode() {
    return Objects.hash(field1, field2, field3);
}

// Or for custom implementation
@Override
public int hashCode() {
    int result = 17;
    result = 31 * result + field1.hashCode();
    result = 31 * result + field2.hashCode();
    return result;
}
```

#### ✅ Key Design Guidelines
- **Use immutable objects** as keys (String, Integer, etc.)
- **Override both `equals()` and `hashCode()`** for custom objects
- **Ensure consistent hashing** across object lifecycle

#### ✅ Performance Optimization
```java
// Specify initial capacity if size is known
Map<String, Integer> map = new HashMap<>(1000);

// Use appropriate load factor for your use case
Map<String, Integer> map = new HashMap<>(100, 0.6f);
```

### 🛡️ Thread Safety Considerations

| **Scenario** | **Recommended Solution** | **Performance** |
|--------------|-------------------------|-----------------|
| **Single-threaded** | `HashMap` | Best performance |
| **Read-heavy multithreaded** | `Collections.synchronizedMap()` | Moderate overhead |
| **Write-heavy multithreaded** | `ConcurrentHashMap` | Optimized for concurrency |

---

## 🧠 Part 10: Interview Questions & Problem Patterns

### 🎯 Classic Hash Table Interview Problems

| **Problem** | **Difficulty** | **Key Insight** | **Pattern** |
|-------------|----------------|-----------------|-------------|
| **🔢 Two Sum** | Easy | Use complement lookup | Hash for O(1) lookup |
| **📝 Group Anagrams** | Medium | Group by sorted string | Hash as grouping key |
| **💾 LRU Cache** | Medium | Combine HashMap + Doubly LinkedList | Fast access + ordering |
| **🔤 First Non-Repeating Character** | Easy | Count frequencies | Frequency counting |
| **🔄 Longest Substring Without Repeating** | Medium | Sliding window + character tracking | Window with hash tracking |
| **🎯 Subarray Sum Equals K** | Medium | Prefix sum technique | Cumulative sum lookup |
| **🔍 Contains Duplicate** | Easy | Check existence | Simple membership test |
| **🏆 Top K Frequent Elements** | Medium | Frequency count + sorting | Count then rank |

### 💡 Problem-Solving Patterns

#### 🔑 Pattern 1: Fast Lookup & Existence Check
```java
// Template: Check if element exists
Set<Integer> seen = new HashSet<>();
for (int num : array) {
    if (seen.contains(target - num)) {
        // Found pair that sums to target
        return true;
    }
    seen.add(num);
}
```

#### 📊 Pattern 2: Frequency Counting
```java
// Template: Count frequencies
Map<Character, Integer> freq = new HashMap<>();
for (char c : string.toCharArray()) {
    freq.put(c, freq.getOrDefault(c, 0) + 1);
}
```

#### 🔄 Pattern 3: Grouping/Categorization
```java
// Template: Group by some property
Map<String, List<String>> groups = new HashMap<>();
for (String word : words) {
    String key = computeKey(word); // e.g., sorted chars for anagrams
    groups.computeIfAbsent(key, k -> new ArrayList<>()).add(word);
}
```

### 🎪 Advanced Interview Topics

| **Topic** | **When It Comes Up** | **Key Points** |
|-----------|----------------------|----------------|
| **Custom Hash Functions** | System design questions | Distribution, collision handling |
| **Consistent Hashing** | Distributed systems | Load balancing, minimal rehashing |
| **Bloom Filters** | Space-efficient membership | Probabilistic, false positives |
| **Hash Table Implementation** | Low-level design | Array, collision resolution, resizing |

---

## ✅ Final Mastery Checklist

| **Concept** | **Understanding Level** | **Can Explain** | **Can Implement** |
|-------------|------------------------|-----------------|-------------------|
| 🏗️ **Key-value storage concept** | ✅ | ✅ | ✅ |
| 🔧 **Hash functions & properties** | ✅ | ✅ | ✅ |
| ⚠️ **Collision resolution methods** | ✅ | ✅ | ✅ |
| ☕ **Java HashMap internals** | ✅ | ✅ | ✅ |
| 📊 **Load factor & rehashing** | ✅ | ✅ | ✅ |
| ⏱️ **Time & space complexity** | ✅ | ✅ | ✅ |
| 🛡️ **Best practices & pitfalls** | ✅ | ✅ | ✅ |
| 🌍 **Real-world applications** | ✅ | ✅ | ✅ |
| 🧠 **Interview problem patterns** | ✅ | ✅ | ✅ |

---

## 🎯 Key Takeaways

✅ **Hash Tables**: Provide O(1) average-case performance for search, insert, and delete operations

✅ **Hash Functions**: Must be deterministic, fast, and provide uniform distribution to minimize collisions

✅ **Collision Resolution**: Chaining (linked lists) vs Open Addressing (probing) each have trade-offs

✅ **Load Factor**: Critical metric (typically 0.75) that triggers rehashing to maintain performance

✅ **Java HashMap**: Evolved from simple chaining to hybrid approach with balanced trees for collision handling

✅ **Real-World Usage**: Essential for caching, counting, grouping, and fast lookups in countless applications

✅ **Interview Success**: Master the core patterns - lookup, frequency counting, and grouping problems

---

*Master Hash Tables and unlock the power of O(1) operations in your algorithms!* 🚀
