# Van Emde Boas Tree (vEB Tree) in C++

## Introduction

This repository contains my **CS201 – Data Structures Project**:  
an optimized and space-efficient implementation of the **Van Emde Boas (vEB) Tree** in C++.

The implementation supports the following operations in:

\[
O(\log \log U)
\]

time complexity, where \(U\) is the universe size.

Supported operations:
- Insert
- Delete
- Member Search
- Successor
- Predecessor
- Minimum
- Maximum

---

## Features

- Fully functional Van Emde Boas Tree implementation
- Sparse representation using custom hash maps for clusters
- Multiple performance optimizations:
  - **Bitmask mode** for very small universes
  - **Array mode** for medium universes
  - **Recursive sparse vEB structure** for large universes
- Interactive menu-driven interface for testing and experimentation

---

## Key Optimizations

### 1. Small Universe Mode (\(U \le 64\))

Uses a 64-bit bitmask representation.

#### Advantages
- Extremely fast operations using bit manipulation
- Very low memory usage

#### Techniques Used
- `__builtin_ctzll`
- `__builtin_clzll`

These built-in functions enable efficient:
- minimum
- maximum
- successor
- predecessor queries

---

### 2. Medium Universe Mode (\(64 < U \le 256\))

Uses a compact byte-array representation.

#### Advantages
- Simpler implementation
- Efficient for moderate universe sizes
- Fast linear scans for:
  - minimum
  - maximum
  - successor
  - predecessor

---

### 3. Large Universe Mode (Sparse Recursive vEB)

Implements the recursive Van Emde Boas structure while optimizing memory usage.

#### Optimizations
- Clusters are created **only when required**
- Sparse storage reduces memory overhead significantly
- Summary tree tracks non-empty clusters efficiently

---

## Data Structures Used

- Recursive Van Emde Boas Tree
- Custom chained hash map for sparse cluster storage
- Bit manipulation techniques for constant-time low-level operations

---

## Time Complexity

| Operation      | Complexity |
|----------------|------------|
| Insert         | \(O(\log \log U)\) |
| Delete         | \(O(\log \log U)\) |
| Search/Member  | \(O(\log \log U)\) |
| Successor      | \(O(\log \log U)\) |
| Predecessor    | \(O(\log \log U)\) |
| Minimum        | \(O(1)\) |
| Maximum        | \(O(1)\) |

---

## Project Structure

```text
.
├── src/
│   └── van_emde_boas_tree.cpp
├── README.md
└── .gitignore