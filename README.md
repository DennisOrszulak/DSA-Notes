# DSA Notes
My notes from Ray Wenderlich's Data Structures and Algorithms book.

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
  * [Binary Trees](#binary-trees)
  * [Binary Search Trees](#binary-search-trees)
  * [AVL Trees](#avl-trees)
  * [Tries](#tries)
  * [Binary Search](#binary-search)
  * [Heaps](#heaps)
  * [Priority Queues](#priority-queues)
* [Sorting Algorithms](#sorting-algorithms)
  * [Bubble Sort](#bubble-sort)
  * [Selection Sort](#selection-sort)
  * [Insertion Sort](#insertion-sort)
  * [Generalization](#generalization)
  * [Merge Sort](#merge-sort)
  * [Radix Sort](#radix-sort)
  * [Heap Sort](#heap-sort)
  * [Quick Sort](#quick-sort)

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

<img src="https://github.com/DennisOrszulak/DSA-Notes/blob/master/DSA%20Notes%20Images/Linked%20List.png" width="400" height="250">


### Stacks

A stack data structure is conceptually a stack of objects, like a deck of cards. They use LIFO (last-in first-out) ordering. When you add (push) an item, it goes on the top. When you remove (pop) an item, it always removes the top-most item. Simple recursion implicitly uses a stack.

### Queues

A queue is a linear structure of elements that are waiting to be processed. It uses FIFO (first-in first-out) ordering. Queues are used when you need to maintain the order of your elements so you can process them later. When you add an element (enqueue), it gets added onto the back of the queue. When you remove an element, it removes the element from the front of the queue. You can also check what's at the front/back of the queue (peek). 

<img src="https://github.com/DennisOrszulak/DSA-Notes/blob/master/DSA%20Notes%20Images/Queue.png" width="400" height="250">

## Trees

A tree is a data structure that simulates a hierarchal structure (like a tree with a root, some branches, and leaves). It’s made out of a collection of nodes that save some data to keep track of its children nodes. The top-most node (the only node that has no parent node) is called the root and it’s the start of the tree. A node that has no children is a leaf. There are different type of trees that have their own unique rules. A tree can be perfectly balanced (every level of the tree is symmetrical and filled with nodes, but this is rare), balanced (every level is filled except for the bottom level), and unbalanced (multiple levels are not symmetric).

**Iterating Through Trees**

There are tons of different ways to traverse a tree, but that depends on the type of tree. The two basic ways to traverse a tree data structure are depth-first and breadth-first.

- Depth-first: Starts at the root, and visits nodes as deep as it can before backtracking. 
- Breadth-first/level-order: Visits each node of the tree based on the depth or level. The root would be considered level 0, then the root’s children nodes would be level 1, and so on…

### Binary Trees

A type of tree where each node can only have a max of two children, and they are referred to as the left and right children. Considerably unbalanced trees affect performance, so try to keep the trees balanced on each side, The picture below is a simple example of an unbalanced vs. balanced tree.

<img src="https://github.com/DennisOrszulak/DSA-Notes/blob/master/DSA%20Notes%20Images/Unbalanced%20Tree%20Example.png" width="450" height="250">

**Traversal**

- In-order: Start from the root node, visit all the nodes in the left subtree, then the root node, then visit all the nodes in the right subtree. It basically goes all the way down to the lower-left-most node, and works it way to the left. This algorithm can find the nodes in ascending order if the nodes are inserted and structured in a certain way.

<img src="https://github.com/DennisOrszulak/DSA-Notes/blob/master/DSA%20Notes%20Images/In-order%20Binary%20Tree%20Traversal.png" width="300" height="250">

- Pre-order: Visit the root node, then visit all the nodes in the left subtree, then visit all the nodes in the right subtree.

<img src="https://github.com/DennisOrszulak/DSA-Notes/blob/master/DSA%20Notes%20Images/Pre-order%20Binary%20Tree%20Traversal.png" width="300" height="250">

- Post-order: Only visit the current node after the left and right children have been visited. The root node is always visited last. 

<img src="https://github.com/DennisOrszulak/DSA-Notes/blob/master/DSA%20Notes%20Images/Post-order%20Binary%20Tree%20Traversal.png" width="300" height="250">

### Binary Search Trees

A BST is a data structure that helps with fast lookup, insert, and removal operations.  These trees are created in a way that cuts the problem in half each time. So once you make a decision, there is no backtracking or looping throughout the other branches of the tree. Then you keep picking a choice until you end up at a leaf node. The BST uses two rules: the value of a left child must be less than the value of its parent, and the value of a right child must be greater than or equal to the value of its parent. The rules setup the tree so that there’s no unnecessary checking, so the average time complexity of lookups, inserts, and removals are O(log n), which are faster than arrays. 

**Lookup**

Since the trees are already sorted based on the two rules, it’s faster than an unsorted array. In an unsorted array, you’d have to check every element, whereas a BST can cut the search space in half each time. The following picture is an example of a BST lookup conceptually. 

<img src="https://github.com/DennisOrszulak/DSA-Notes/blob/master/DSA%20Notes%20Images/BST%20Lookup%20Example.png" width="300" height="250">

**Insertion**

Inserting values are very easy with binary search trees. Since the tree is already sorted, you don’t have to move any previous values from their locations (like inserting a number into the beginning of an array where you have to shift everything over 1 spot). Just keep traversing through the tree based on the rules until you hit a leaf node, and insert the value on the left (if the value’s smaller than the leaf node) or on the right (if the value’s larger than the leaf node). The picture below is an example of an insertion conceptually. 

<img src="https://github.com/DennisOrszulak/DSA-Notes/blob/master/DSA%20Notes%20Images/BST%20Insert%20Example.png" width="300" height="250">

**Removal**

Removals can be trickier to implement. If the node you’re removing is a leaf node, just remove that node. If the node you’re removing only has 1 child, just reconnect the child node to the rest of the tree (which should be the parent node of the node that you removed). If the node has 2 children, you’ll have to perform a node swap. Replace the removed node with the smallest node (leftmost) in its right subtree. For example in the following pictures, if you want to remove the value 25, replace it with 27. The removed node’s parent (50) only has space for 1 more child, so you can’t connect 12 and 37 back to the root or you’d break the BST rules and break the tree. If you move the smallest node in the removed node’s subtree (27), the tree will still follow the rules. Make sure to delete 27 from the original spot so it’s not duplicated in the tree.

<img src="https://github.com/DennisOrszulak/DSA-Notes/blob/master/DSA%20Notes%20Images/BST%20Remove%20Value%20Example.png" width="300" height="250">

<img src="https://github.com/DennisOrszulak/DSA-Notes/blob/master/DSA%20Notes%20Images/BST%20Remove%20Value%20Swap.png" width="300" height="250">

### AVL Trees

Georgy Adelson-Velsky and Evgenii Landis came up with the first self-balancing binary search tree called the AVL Tree. 

**Measuring Balance**

The AVL tree measures the balance of the whole tree by applying a height property to each node. The height of a node is the longest distance from the current node to a leaf node. The balance factor is calculated with the height difference of the left and right child. If a child is nil, the height is considered to be -1. A balanced tree should have a balance factor of 1. Below is an example of a balanced tree that shows the height and balance factor.

<img src="https://github.com/DennisOrszulak/DSA-Notes/blob/master/DSA%20Notes%20Images/AVL%20Balance%20And%20Height%20Example.png" width="400" height="250">

Now if you insert 40 (which gets placed as the right child of 37), the tree becomes unbalanced. The balance factor changes to 2 (2 or -2 means it’s unbalanced). Even if more than one node might have a bad balancing factor, you only need to perform the balancing proceed on the bottom-most node containing the bad balance factor. So the node containing 25 will need to be fixed. 

**Rotations**

Rotations are used to balance a binary search tree. There are four different types of rotations (left, left-right, right, right-left), one for each way a tree can become unbalanced.

**Left Rotation**

The problem caused by inserting 40 can be fixed using a left rotation. This causes in-order traversal for the nodes to remain the same, and the depth of the tree is reduced by one level. A generic left rotation example is pictured below. 

<img src="https://github.com/DennisOrszulak/DSA-Notes/blob/master/DSA%20Notes%20Images/AVL%20Left%20Rotation%20Concept.png" width="350" height="250">

To perform a left rotation, the right child is selected as the pivot. This node will replace the rotated node as the root and move up a level. The node to be rotated becomes the left child of the pivot and moves down a level (so the current left child of the pivot has to move somewhere else). The pivot's left child can is set to the rotated node. Update the heights of the rotated node and the pivot. The last step is to return the pivot so that it can replace the rotated node in the tree. 

avl left rotation example
<img src="" width="350" height="250">

**Right Rotation**

A right rotation is the symmetrical opposite of left rotation. When left children are causing an imbalance, complete a right rotation. A generic right rotation example is pictured below. 

avl right rotation generic
<img src="" width="350" height="250">

The steps for complete this rotation is identical to the left rotation, except the references to the left and right children are swapped. 

**Right-left Rotation**

Inserting 36 into the original tree will cause a problem. Doing a left rotation won't result in a balanced tree, so you need to perform a right rotation on the right child before doing the left rotation. Apply a right rotation to the 37 node so that 25, 36, and 37 are all right children. Then apply a left rotation. A right-left rotation example is pictured below. 

right-left rotation example
<img src="" width="350" height="250">

**Left-right Rotation**

A left-right rotation is also the symmetrically opposite of the right-left direction. A left-right rotation example is pictured below.

left-right rotation example
<img src="" width="350" height="250">

**Balance**

A balance factor of 2 means that the left child is heaver (contains more nodes) than the right child. This is where you use a right or left-right rotation. A balance factor of -2 means that the right is heavier than the left, so use a left or right-left rotation. 

### Tries

A trie (pronounced try) is a tree that specializes in storing data that can be represented as a collection (such as english words). Each character in the string is mapped to a node. The last node is a terminating node. 

trie example
<img src="" width="350" height="250">

This data structure has great performance characteristics for situations like finding words that have a matching prefix, since multiple words can share the same characters. Storing thousands of words in an array and searching through that array would be time consuming, so a trie is beneficial. Pictured below is an example of finding all the words that start with 'C' (cut' and 'cute').

trie finding c words example
<img src="" width="350" height="250">

```swift
  // TODO Implementation Section (Insert, Contains, Remove, Matching)
```

### Binary Search

Binary search is one of the most efficient searching algorithms with a time complexity of O(log n), which is the same as searching a balanced binary tree. Two conditions need to be met before a binary search can be used: The collection must be able to manipulate indices in constant time (conform to RandomAccessCollection in Swift), and the collection has to be sorted. 

To use a binary search, first you have to find the middle index of the collection. Check that element, and compare it to the element you're trying to find. If it's the same, then you successfully found it. If value you're searching for is less than the middle value, recursively call the binary search again for the left subsequence. If it's greater, search the right subsequence. Each call basically removes half of the comparisons and you continue doing these steps until you find your answer or you can’t split up the collection, so it's very quick. A binary search for 31 is pictured below.

Binary search example
<img src="" width="350" height="250">

### Heaps

A heap is a complete binary tree (binary heap) that can be constructed with an array. (Not to be confused with memory heaps). There are two types of heaps: Max heap, where the elements with a higher value have a higher priority, and a min heap, where lower value elements have a higher priority. And since a heap is a complete binary tree, every level must be filled with nodes except the last level. 

Heap property
<img src="" width="350" height="250">


The heap property (or invariant) is important. In a max heap, parent nodes always contain nodes that are smaller values, where the root node is the highest value of the tree. A min heap is the opposite. 

Heap levels
<img src="" width="350" height="250">

**Heap Applications**

* Calculating min or max elements of a collection
* Heap sort
* Constructing a priority queue
* Constructing graph algorithms (like Prim or Dijkstra) with a priority queue

**Representing A Heap**

Heaps can be represented with an array, unlike a regular tree. Iterate through each element level-by-level from left to right. As you go to the next level, you’ll have twice as many nodes. The picture below would be the complete array using the previous picture of heap levels. 

Creating heap array 
<img src="" width="350" height="250">

You can access the nodes by using simple equations. Given a node at a zero-based index i, the left child of the node can be found at index (2i + 1) and the right child index is at (2i + 2). To get the parent of a node, you can solve for i. Given a child node at index i, that child's parent node is at index ((i - 2) / 2).

**Removing Top Element**

This removes the root node from the heap. In this max heap example, 10 will be removed. Swap the root node with the last element.

heap remove 1
<img src="" width="350" height="250">

Remove the last element and save its value so you can place it back later, then check to see if it still follows the rule for a max heap (children nodes have to be smaller than the parent node). 

heap remove 2
<img src="" width="350" height="250">

Since the heap doesn't follow that rule now, you have to perform a sift down. Start from the current value 3 and check its children. If 1 child has a value that's bigger, swap them. If both children are bigger, swap it with the biggest value. Keep doing this until both children have a smaller value. So for this example, the first sift will swap 3 and 8, and then 6 and 3. The final heap is pictured below

heap remove 3
<img src="" width="350" height="250">

**Removing Any Element**

To remove any element, check if the index is within the bounds of the array. If you want to remove the last element, just remove it. If you're not removing the last element, swap the element with the last element, return and remove the last element, then perform a sift down and sift up to adjust the heap. The following pictures show an example. 

Heap Removing Any 1
<img src="" width="350" height="250">

heap removing any 2
<img src="" width="350" height="250">

**Inserting Elements**

If you want to insert an element, add it to the end of the heap. For this example, we're going to add 7. 

heap insert 1
<img src="" width="350" height="250">

To find the correct place for the new node, keep sifting up (swap them if the parent node is smaller) until the parent node is bigger. In this example, swap 7 to 4's place, then 7 to 6's place. 

heap insert 2
<img src="" width="350" height="250">

**Searching Elements**

You have to perform a search on the heap if you want the index of an element you want to delete. Heaps aren't designed for fast searches since it uses an array. The worst case operation is O(n) since it might have to check every single element. There are a few steps to searching a heap:
* If the index is greater or equal to the number of elements, you can't search since it's out of bounds. Return nil or an error. 
* Check if the element you're searching for has a higher priority than the current element at index i. If it does, the element can not be lower in the heap because that breaks the heap's rules. 
* If the element is equal to the element at index i, return the index i. 
* Recursively search for the element starting from the left child i, then right child i. The search failed if both of those fail to return an index. Return nil or an error. 

**Operations and Time Complexities Summary**

heap time complexities
<img src="" width="350" height="250">

### Priority Queues

A priority queue has elements where instead of first-in-first-out order, they come out in order by priority. One type of priority queue is max-priority, where the highest priority is the element at the front, and the other type is a min-priority, where the lowest priority is in the front. These can be useful if you need to find the minimum or maximum values.

**Applications**
* Dijkstra's algorithm - calculates the minimum cost
* A* Pathfinding algorithm - tracks the unexplored routes that have the shortest length
* Heap sort - can be created using a priority queue
* Huffman coding - where a min-priority queue is used to repeatedly find two nodes with the smallest frequency that don't have a parent node

**Operations**

Priority queues have the same operations as a normal queue, but the implementations are a little different since they're based on priority.

* Enqueue - Inserts an element
* Dequeue - Removes the element with the highest priority
* isEmpty - Checks if the queue is empty
* Peek - Returns the element with the highest priority without removing it.

**Creating Priority Queues**

There are few different ways you can implement these types of queues.

* Sorted array - Useful to get the max/min value of an element in O(1) time. Insertions are slow and require O(n) since you have to go through the array in order.
* Balanced binary search tree - Useful for creating a double-ended priority queue to get the min/max value in O(log n) time. Insertion is also the same time. 
* Heap - The natural choice for a priority queue. More efficient than a sorted array because it only needs to be partially sorted. All operations are O(log n) except getting the min/max values which is O(1).

## Sorting Algorithms

### Bubble Sort

### Selection Sort

### Insertion Sort

### Generalization

### Merge Sort

### Radix Sort

### Heap Sort

### Quick Sort










