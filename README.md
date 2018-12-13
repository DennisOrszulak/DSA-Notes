# DSA Notes
My notes from Ray Wenderlich's Data Structures and Algorithms book using Swift.

## Table of Contents

* [Time Complexity](#time-complexity)
  * [Constant Time](#constant-time)
  * [Linear Time](#linear-time)
  * [Quadratic Time](#quadratic-time)
  * [Logarithmic Time](#logarithmic-time)
  * [Quasilinear Time](#quasilinear-time)
  * [Other Time Complexities](#other-time-complexities)
* [Space Complexity](#space-complexity)
* [Basic Data Structures](#basic-data-structures)
  * [Linked Lists](#linked-lists)
  * [Stacks](#stacks)
  * [Queues](#queues)
* [Trees](#trees)
  * [Basic Trees](#basic-tree)
  * [Binary Trees](#binary-trees)
  * [Binary Search Trees](#binary-search-tress)
  * [AVL Trees](#avl-trees)
  * [Tries](#tries)
  * [Binary Search](#binary-search)
  * [Heaps](#heaps)
  * [Priority Queues](#priority-queues)
  
## Time Complexity

Time complexity is a measure of the time required to run an algorithm as the number of inputs increase. It only gives a high-level ranking of the performance, so loops that happen a set number of times or other setup code is not part of the basic calculation. This means that two algorithms can have the same time complexity, but one might be a lot faster due to supporting code or functions. All constants are dropped in the final notation. Time complexity can help predict scalability. Some algorithms use each element (linear, quadratic), but some only need to use a portion of the elements which lead to a faster runtime (logarithmic). 

Below is a chart from [Big O Cheatsheet](http://bigocheatsheet.com/) so you can see the differences between a few time complexities.

![Big O Complexity Chart](/DSA%20Notes%20Images/Big%20O%20Complexity%20Chart.png)

### Constant Time

An algorithm that has the same running time regardless of the size of the input. The Big O notation is O(1).

**Example:**

The size of the array has no effect on the running time, because it just checks the first element of the array.

```swift
func checkFirst(names: [String]) {
    if let first = names.first {
    print(first)
  } else {
    print("no names")
  }
}
```

### Linear Time

An algorithm where the running time increases linearly based on the size of the input. The Big O notation is O(n).

**Example:**

The size of the array has no effect on the running time, because it just checks the first element of the array.

```swift
func printAllNames(names: [String]) {
    for name in names {
      print(name)
    }
}
```

### Quadratic Time

An algorithm where the running time is proportional to the square of the input size. It is one of the worst time complexities to have. The Big O notation is O(n^2).

**Example:**

The function prints out all the names for every name in the array. So if you have 5 names, it'll print the 5 names 5 times for a total of 25 print statements.

```swift
func printAllNames(names: [String]) {
    for _ in names {
      for name in names {
        print(name)
      }
    }
    
}
```

### Logarithmic Time

An algorithm where as the size of the inputs increase, the time it takes to execute barely increases. This could be done by reducing the amount of executions you need to do (like halving the data  in a Binary search). The Big O notation is O(log n).

**Example:**

The function only checks half of the array to come up with the answer. It checks the middle value and decides whether it will look at the next values (values to the right on a number line) or previous values (values to the left).

```swift
func naiveContains(_ value: Int, in array: [Int]) -> Bool {
    guard !array.isEmpty else { return false }
    let middleIndex = array.count / 2
 
    if value <= array[middleIndex] {
      for index in 0...middleIndex {
        if array[index] == value {
          return true
        }
      }
    } else {
      for index in middleIndex..<array.count {
        if array[index] == value {
          return true
        }
      }
    }
 
    return false
}
```

### Quasilinear time

These perform worse than linear, but a lot better than quadratic. The big O notation is O(n log n).

### Other Time Complexities

Other time complexities exist such as polynomial, exponential, and factorial. The previous 5 are usually the most common. 

## Space Complexity

Space complexity is a measure of the resources required for an algorithm to run. Memory is a major factor in computing, so managing memory during computations is also important for predicting scalability.

## Basic Data Structures

These form the basis of more advanced algorithms. 

### Linked Lists

A linked list is a collection of values stored in a linear unidirectional sequence. It's basically a chain of nodes, and each node holds a value and a reference to the next node. The head of the list is the first element and the tail is the last element. A nil reference means that it's the end of the list. A doubly linked list means that there are references to the next node and also the previous node, so you can have bidirectional movement.

![Linked List](/DSA%20Notes%20Images/Linked%20List.png)

**Example:**

```swift
  // TODO
```

### Stacks

A stack data structure is conceptually a stack of objects, like a deck of cards. They use LIFO (last-in first-out) ordering. When you add (push) an item, it goes on the top. When you remove (pop) an item, it always removes the top-most item. Simple recursion implicitly uses a stack.

**Example:**

```swift
  // TODO
```

### Queues

A queue is a linear structure of elements that are waiting to be processed. It uses FIFO (first-in first-out) ordering. Queues are used when you need to maintain the order of your elements so you can process them later. When you add an element (enqueue), it gets added onto the back of the queue. When you remove an element, it removes the element from the front of the queue. You can also check what's at the front/back of the queue (peek). 

![Queue](/DSA%20Notes%20Images/Queue.png)

**Example:**

```swift
  // TODO
```

## Trees

A tree is a data structure that simulates a hierarchal structure (like a tree with a root, some branches, and leaves). It’s made out of a collection of nodes that save some data to keep track of its children nodes. The top-most node (the only node that has no parent node) is called the root and it’s the start of the tree. A node that has no children is a leaf. There are different type of trees that have their own unique rules. 

**Iterating Through Trees**

There are tons of different ways to traverse a tree, but that depends on the type of tree. The two basic ways to traverse a tree data structure are depth-first and breadth-first.

- Depth-first: Starts at the root, and visits nodes as deep as it can before backtracking. 
- Breadth-first/level-order: Visits each node of the tree based on the depth or level. The root would be considered level 0, then the root’s children nodes would be level 1, and so on…

### Binary Trees

A type of tree where each node can only have a max of two children, and they are referred to as the left and right children. Considerably unbalanced trees affect performance, so try to keep the trees balanced on each side, The picture below is a simple example of an unbalanced vs. balanced tree.

![Unbalanced Tree](/DSA%20Notes%20Images/Unbalanced%20Tree%20Example.png)

**Traversal**

- In-order: Start from the root node, visit all the nodes in the left subtree, then the root node, then visit all the nodes in the right subtree. It basically goes all the way down to the lower-left-most node, and works it way to the left. This algorithm can find the nodes in ascending order if the nodes are inserted and structured in a certain way.

![Traversal](/DSA%20Notes%20Images/In-order%20Binary%20Tree%20Traversal.png)

- Pre-order: Visit the root node, then visit all the nodes in the left subtree, then visit all the nodes in the right subtree.

![Traversal](/DSA%20Notes%20Images/Pre-order%20Binary%20Tree%20Traversal.png)

- Post-order: Only visit the current node after the left and right children have been visited. The root node is always visited last. 

![Traversal](/DSA%20Notes%20Images/Post-order%20Binary%20Tree%20Traversal.png)

### Binary Search Trees

A BST is a data structure that helps with fast lookup, insert, and removal operations.  These trees are created in a way that cuts the problem in half each time. So once you make a decision, there is no backtracking or looping throughout the other branches of the tree. Then you keep picking a choice until you end up at a leaf node. The BST uses two rules: the value of a left child must be less than the value of its parent, and the value of a right child must be greater than or equal to the value of its parent. The rules setup the tree so that there’s no unnecessary checking, so the average time complexity of lookups, inserts, and removals are O(log n), which are faster than arrays. 

**Lookup**

Since the trees are already sorted based on the two rules, it’s faster than an unsorted array. In an unsorted array, you’d have to check every element, whereas a BST can cut the search space in half each time. The following picture is an example of a BST lookup conceptually. 

![BST](/DSA%20Notes%20Images/BST%20Lookup%20Example.png)

**Insertion**

Inserting values are very easy with binary search trees. Since the tree is already sorted, you don’t have to move any previous values from their locations (like inserting a number into the beginning of an array where you have to shift everything over 1 spot). Just keep traversing through the tree based on the rules until you hit a leaf node, and insert the value on the left (if the value’s smaller than the leaf node) or on the right (if the value’s larger than the leaf node). The picture below is an example of an insertion conceptually. 

![BST](/DSA%20Notes%20Images/BST%20Insert%20Example.png)

**Removal**

Removals can be trickier to implement. If the node you’re removing is a leaf node, just remove that node. If the node you’re removing only has 1 child, just reconnect the child node to the rest of the tree (which should be the parent node of the node that you removed). If the node has 2 children, you’ll have to perform a node swap. Replace the removed node with the smallest node (leftmost) in its right subtree. For example in the following pictures, if you want to remove the value 25, replace it with 27. The removed node’s parent (50) only has space for 1 more child, so you can’t connect 12 and 37 back to the root or you’d break the BST rules and break the tree. If you move the smallest node in the removed node’s subtree (27), the tree will still follow the rules. Make sure to delete 27 from the original spot so it’s not duplicated in the tree.

![BST](/DSA%20Notes%20Images/BST%20Remove%20Value%20Example.png)

![BST](/DSA%20Notes%20Images/BST%20Remove%20Value%20Swap.png)
















