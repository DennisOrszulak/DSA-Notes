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

A linked list is a collection of values stored in a linear unidirectional sequence. It's basically a chain of nodes, and each node holds a value and a reference to the next node. A nil value for a reference means that it's the end of the list. 

**Example:**

```swift
  // TODO
```

### Stacks

A stack data structure is conceptually a stack of objects, like a deck of cards. They use LIFO (last-in first-out) ordering. When you add (push) an item, it goes on the top. When you remove (pop) an item, it always removes the top-most item.

**Example:**

```swift
  // TODO
```

### Queues

A queue is a linear structure of elements that are waiting to be processed. It uses FIFO (first-in first-out) ordering. Queues are used when you need to maintain the order of your elements so you can process them later. When you add an element (enqueue), it gets added onto the back of the queue. When you remove an element, it removes the element from the front of the queue. You can also check what's at the front/back of the queue (peek).

**Example:**

```swift
  // TODO
```














